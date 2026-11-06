# ERP Integration Matrix

## 1. Purpose

This document defines how all Smart ERP modules communicate, exchange data, and interact with the central accounting system.

Its primary objectives are:
- Define clear ownership and responsibilities for each business process.
- Prevent duplicate transactions and duplicate accounting entries.
- Establish consistent document flows between modules.
- Ensure accurate and traceable financial postings.
- Maintain data integrity across companies, branches, and tenants.
- Provide a unified integration framework for all current and future modules.

## 2. Core Integration Principles

### 2.1 Single Source of Truth
Each business transaction must have one owning module responsible for its original business document and operational data.

Other modules may consume, reference, or process that data but must not create duplicate versions of the same transaction.

### 2.2 Central Accounting Engine
All financial transactions must be processed through a centralized Accounting Posting Engine integrated with the General Ledger.

Operational modules must not independently create uncontrolled or duplicate General Ledger entries.

The Accounting Posting Engine must:
- Receive approved accounting events from source modules.
- Identify the applicable accounting rules.
- Determine accounts based on company configuration and transaction context.
- Validate account mappings and required dimensions.
- Generate balanced journal entries.
- Submit entries through the configured approval and posting workflow.
- Maintain complete references to source documents.
- Prevent duplicate accounting events and duplicate postings.

### 2.3 Standard Integration References
Every integrated transaction must maintain:
- Tenant ID.
- Group ID, where applicable.
- Company ID.
- Branch ID, where applicable.
- Source Module.
- Source Document Type.
- Source Document ID.
- Source Transaction ID.
- Accounting Event ID, where applicable.
- Created By and Approved By.
- Transaction Date and Posting Date.

### 2.4 Transaction Integrity
- Related operations must use appropriate database transactions.
- Financial posting must be atomic.
- Failed transactions must not leave incomplete accounting records.
- Integration requests must support idempotency to prevent duplicate processing.
- Reversals must reference the original transaction.
- Historical posted transactions must remain traceable and protected.

## 3. Module Ownership Matrix

| Business Function | Primary Owning Module | Integrated Modules |
|---|---|---|
| Customer Master Data | Business Partner / AR-AP | Sales, Treasury, CRM |
| Supplier Master Data | Business Partner / AR-AP | Procurement, Treasury, Import |
| Sales Orders | Sales | Inventory, AR, Manufacturing |
| Sales Invoices | AR / Sales | GL, Inventory, Tax |
| Customer Receipts | Treasury | AR, GL |
| Purchase Orders | Procurement | Inventory, Import, Budgeting |
| Goods Receipt Notes | Inventory / Procurement | AP, GL, Import |
| Supplier Invoices | AP / Procurement | GL, Inventory, Tax, Import |
| Supplier Payments | Treasury | AP, GL |
| Inventory Movements | Inventory | Sales, Procurement, Manufacturing, GL |
| Inventory Valuation | Inventory Costing | GL, Management Reporting |
| Production Orders | Manufacturing | Inventory, Cost Accounting |
| Production Costing | Manufacturing | Inventory, GL, Cost Accounting |
| Fixed Asset Register | Fixed Assets | GL, Treasury, Procurement |
| Depreciation | Fixed Assets | GL |
| Bank Transactions | Treasury | AR, AP, GL |
| Payroll Calculations | HR / Payroll | Treasury, GL |
| Employee Advances | HR / Payroll | Treasury, GL |
| Tax Calculations | Tax Management | AR, AP, Payroll, GL |
| Financial Journals | General Ledger | All Accounting-Enabled Modules |
| Consolidation | Group Consolidation | GL, Intercompany, Reporting |
| Budget Management | Budgeting & Planning | All Relevant Modules |

## 4. Standard Business Process Integration Flows

### 4.1 Sales Process

Quotation → Sales Order → Credit Check → Inventory Reservation → Delivery Note → Sales Invoice → Customer Receipt → Invoice Settlement.

Responsibilities:
- Sales manages quotations and sales orders.
- Inventory manages stock reservation and goods issue.
- AR manages customer invoices, balances, and settlement.
- Tax Management calculates applicable taxes.
- Treasury manages receipt of funds.
- General Ledger receives accounting events through the Accounting Posting Engine.

Accounting examples:

Sales invoice:
- Debit: Accounts Receivable.
- Credit: Sales Revenue.
- Credit: Output Tax, where applicable.

Inventory issue:
- Debit: Cost of Goods Sold.
- Credit: Inventory.

Customer receipt:
- Debit: Bank or Cash.
- Credit: Accounts Receivable.

The exact accounts and tax treatment must follow company configuration and applicable accounting rules.

### 4.2 Procurement Process

Purchase Requisition → RFQ → Supplier Quotation → Purchase Order → Goods Receipt Note → Supplier Invoice → Payment → Invoice Settlement.

Responsibilities:
- Procurement manages purchasing documents and purchase orders.
- Inventory manages receipt, inspection, and stock records.
- AP manages supplier invoices and outstanding balances.
- Treasury manages payments.
- Tax Management handles applicable tax treatment.
- General Ledger receives accounting events through the Accounting Posting Engine.

Typical accounting events:

Goods received before supplier invoice:
- Debit: Inventory.
- Credit: Goods Received Not Invoiced (GRNI).

Supplier invoice:
- Debit: GRNI and applicable price differences or expenses.
- Debit: Recoverable Input Tax, where applicable.
- Credit: Accounts Payable.

Supplier payment:
- Debit: Accounts Payable.
- Credit: Bank or Cash.

The system must support service purchases, non-stock purchases, partial receipts, partial invoices, and three-way matching.

### 4.3 Inventory Process

Inventory Receipt → Inspection → Put Away → Stock Movement → Reservation → Issue / Transfer / Return → Stock Valuation.

Responsibilities:
- Inventory owns quantity movements and stock balances.
- Inventory Costing calculates inventory valuation.
- Procurement and Manufacturing provide source documents.
- Sales provides delivery and return requests.
- General Ledger receives approved inventory accounting events.

The system must distinguish:
- Physical quantity.
- Available quantity.
- Reserved quantity.
- In-transit quantity.
- Owned inventory.
- Inventory held on behalf of third parties.
- Inventory valuation.

Inventory movements must not create duplicate accounting entries when the same source transaction is already posted.

### 4.4 Manufacturing Process

Production Demand → Production Order → Material Reservation → Material Issue → Work in Progress → Production Completion → Finished Goods Receipt.

Responsibilities:
- Manufacturing owns production orders and execution.
- Inventory manages material issues, returns, and finished goods receipts.
- Manufacturing Costing calculates production costs and variances.
- General Ledger records approved accounting events.

Typical accounting events:

Material issue:
- Debit: Work in Progress.
- Credit: Raw Materials Inventory.

Production completion:
- Debit: Finished Goods Inventory.
- Credit: Work in Progress.

Production variances must be calculated and posted according to the configured costing method and accounting policy.

### 4.5 Fixed Assets Process

Purchase / Asset Acquisition → Asset Recognition → Capitalization → Depreciation → Revaluation / Impairment → Disposal.

Responsibilities:
- Procurement manages purchase documents.
- Fixed Assets owns the asset register and asset lifecycle.
- Treasury manages related payments.
- General Ledger records acquisition, depreciation, impairment, and disposal entries.

Typical accounting events:

Asset capitalization:
- Debit: Fixed Assets.
- Credit: Accounts Payable, GRNI, or another applicable clearing account.

Depreciation:
- Debit: Depreciation Expense.
- Credit: Accumulated Depreciation.

Asset disposal must calculate the carrying amount and resulting gain or loss.

### 4.6 Treasury and Banking Process

Payment Request → Approval → Payment Execution → Bank Transaction → Reconciliation → Settlement.

Responsibilities:
- Treasury owns cash and bank transactions.
- AR/AP owns customer and supplier balances.
- Treasury records and executes payments and receipts.
- AR/AP manages invoice allocation and outstanding balances.
- General Ledger records the resulting accounting entries.

A payment must not be considered settled against an invoice until the relevant allocation is successfully recorded.

### 4.7 HR and Payroll Process

Employee Records → Attendance → Leave → Payroll Calculation → Payroll Approval → Payment → Accounting Posting.

Responsibilities:
- HR owns employee records.
- Attendance manages time and attendance information.
- Payroll calculates salaries, deductions, and employer contributions.
- Treasury executes salary payments.
- General Ledger records payroll expenses and liabilities.

Typical payroll accounting:
- Debit: Salary and Related Expenses.
- Credit: Net Salary Payable.
- Credit: Tax and Social Insurance Payables.
- Credit: Other Employee Deductions Payable.

Employer contributions must be recorded according to applicable rules.

### 4.8 Import Process

Purchase Order → Import File → Letter of Credit / Advance Payment → Shipment Tracking → Customs Clearance → Goods Receipt → Landed Cost Allocation → Supplier Invoice Settlement.

Responsibilities:
- Procurement owns the purchase order.
- Import Management owns shipment documentation and import tracking.
- Treasury owns bank payments, letters of credit, and related bank transactions.
- Inventory owns received quantities and inventory valuation.
- AP owns supplier invoices and balances.
- General Ledger receives approved accounting events.

Import Management must not create duplicate purchase invoices or duplicate supplier balances.

Eligible landed costs must be allocated to inventory according to the configured accounting policy.

## 5. Accounting Event Framework

All modules that generate financial transactions must submit standardized accounting events.

Each accounting event must contain:
- Event ID.
- Source Module.
- Source Document ID.
- Event Type.
- Company ID.
- Branch ID, where applicable.
- Transaction Date.
- Posting Date.
- Transaction Currency.
- Functional Currency.
- Exchange Rate.
- Accounting Dimensions.
- Debit and Credit information.
- Tax information, where applicable.
- Approval Status.
- Reversal Reference, where applicable.

The Accounting Posting Engine must validate:
1. Source document approval.
2. Valid company and tenant context.
3. Open accounting period.
4. Valid and active accounts.
5. Required accounting dimensions.
6. Balanced journal entries.
7. Correct currency conversion.
8. Duplicate event prevention.
9. User authorization and approval requirements.

Only successfully validated events may proceed to journal creation and posting.

## 6. Intercompany Integration

The system must support transactions between companies belonging to the same group.

Requirements:
- Identify intercompany counterparties.
- Link both sides of an intercompany transaction.
- Maintain reciprocal transaction references.
- Support intercompany sales and purchases.
- Support intercompany loans and settlements.
- Support intercompany balances reconciliation.
- Identify differences between counterpart company records.
- Support elimination entries during consolidation.
- Maintain an audit trail for intercompany adjustments.

Intercompany transactions must preserve the original company-level accounting records.

Consolidation eliminations must not modify the original company ledgers.

## 7. Multi-Currency Integration

Each company must maintain its functional currency.

The system must support:
- Transaction Currency.
- Functional Currency.
- Group Presentation Currency.
- Historical Exchange Rates.
- Period-End Exchange Rates.
- Realized and Unrealized Exchange Differences.
- Foreign Currency Revaluation.
- Consolidation Currency Translation.

Exchange rates must be stored with their source, effective date, and approval history where required.

Currency conversion and rounding rules must be consistent across all modules.

## 8. Central Workflow and Approval Integration

All modules should use a shared workflow framework.

The workflow framework must support:
- Configurable approval levels.
- Amount-based approval limits.
- Company and branch-specific rules.
- Role-based approvals.
- Maker-Checker controls.
- Segregation of Duties.
- Rejection and resubmission.
- Delegation with authorization.
- Escalation rules.
- Complete approval history.

Approval requirements must be configurable without changing the underlying business logic.

## 9. Document and Attachment Integration

A centralized Document Management service should support:
- Document uploads and storage.
- Document classification.
- Links to business transactions.
- Version history.
- Access permissions.
- Document expiry alerts.
- Secure download and retrieval.
- Audit logs.

Documents must be linked to their source transactions rather than duplicated unnecessarily across modules.

## 10. Integration Error Handling

The integration framework must:
- Record failed integration requests.
- Maintain error codes and descriptions.
- Support controlled retry operations.
- Prevent duplicate processing during retries.
- Provide monitoring for failed and pending events.
- Support authorized manual intervention.
- Maintain complete integration history.

Financial transactions must never be silently discarded or marked successful when the related accounting operation has failed.

## 11. Reporting and Reconciliation

The system must provide:
- Subledger-to-General-Ledger reconciliation.
- Inventory-to-General-Ledger reconciliation.
- Fixed Assets-to-General-Ledger reconciliation.
- Payroll-to-General-Ledger reconciliation.
- Bank-to-General-Ledger reconciliation.
- Intercompany balance reconciliation.
- GRNI reconciliation.
- WIP reconciliation.
- Integration failure reports.
- Unposted accounting events reports.

All reconciliation reports must support filtering by tenant, group, company, branch, period, and source module where applicable.

## 12. Security and Tenant Isolation

- Every integration request must carry a validated tenant context.
- Tenant context must be obtained from authenticated server-side identity and authorization, not trusted directly from client input.
- Cross-tenant data access must be prohibited.
- Intercompany transactions must only operate within authorized group relationships.
- Background jobs must preserve tenant and company context.
- API integrations must enforce authentication, authorization, and audit logging.
- Sensitive financial data must be protected according to access policies.

## 13. Integration Testing Requirements

The system must include automated tests for:
- Successful integration between all major modules.
- Duplicate accounting event prevention.
- Failed posting and controlled retry.
- Partial receipts and partial invoices.
- Partial payments and payment allocation.
- Inventory valuation and accounting reconciliation.
- Manufacturing WIP and production costing.
- Fixed asset depreciation and disposal.
- Payroll accounting and payment reconciliation.
- Multi-currency transactions.
- Intercompany transactions and consolidation eliminations.
- Closed accounting periods.
- Unauthorized cross-tenant access.
- Concurrent processing and transaction integrity.

## 14. Implementation Principle

The integration architecture must be implemented incrementally.

The first release must establish:
1. Tenant and company context.
2. Business Partner Master Data.
3. Chart of Accounts.
4. General Ledger.
5. Central Accounting Posting Engine.
6. Basic AR/AP integration.
7. Basic Treasury integration.

Additional modules must integrate through the same standardized framework.

No module should introduce an independent accounting posting mechanism that bypasses the central Accounting Posting Engine.
