# Smart ERP – General Ledger & Journal Entries
**Version:** 1.0

## 1. General Design

The General Ledger is the central accounting engine of Smart ERP.

It must support multiple companies, branches, currencies, fiscal years, and configurable approval workflows.

## 2. Journal Entry Sources

The system must support:

- Manual Journal Entries.
- Sales-generated Entries.
- Purchase-generated Entries.
- Cash Receipt Entries.
- Payment Entries.
- Inventory Entries.
- Fixed Asset Depreciation Entries.
- Import Cost Entries.
- Foreign Exchange Entries.
- Other System-generated Entries.

Every automatic entry must reference its originating transaction.

Duplicate posting of the same source transaction must be prevented.

## 3. Journal Entry Workflow

Supported statuses:

- Draft.
- Submitted.
- Approved.
- Rejected.
- Posted.
- Reversed.

Approval workflows must be configurable by company, transaction type, amount, and user permissions.

## 4. Journal Entry Numbering

- Independent numbering per company.
- Configurable document prefixes.
- Configurable fiscal-year sequences.
- Separate sequences by document type where required.
- Unique and concurrency-safe numbering.

Example: ABC-JV-2026-000001.

## 5. Journal Entry Information

Header fields:

- Journal ID.
- Voucher Number.
- Company.
- Branch.
- Fiscal Year.
- Accounting Period.
- Transaction Date.
- Posting Date.
- Currency.
- Exchange Rate.
- Description.
- Source Type.
- Source Document Reference.
- Created By.
- Approved By.
- Posted By.

Journal lines:

- Account.
- Description.
- Debit Amount.
- Credit Amount.
- Transaction Currency.
- Functional Currency Amount.
- Exchange Rate.
- Analytical Dimensions.
- Reference Information.

## 6. Accounting Validation

- Total debits must equal total credits in functional currency.
- Posting accounts must be active and valid.
- Parent accounts cannot receive direct postings.
- Required analytical dimensions must be completed.
- Posting must be blocked in closed periods.
- Duplicate source transactions must be rejected.
- All posted entries must be immutable.

## 7. Fiscal Period Management

Period statuses:

- Open.
- Soft Closed.
- Hard Closed.

Reopening a closed period requires appropriate authorization and a complete audit trail.

## 8. Reversal and Corrections

Posted entries cannot be edited or deleted.

Corrections must be performed through reversal or adjustment entries linked to the original entry.

The original transaction and its history must remain accessible.

## 9. Multi-Currency Accounting

The system must support:

- Transaction Currency.
- Functional Currency.
- Exchange Rate.
- Foreign Currency Amount.
- Functional Currency Amount.
- Exchange Differences.
- Rounding Adjustments.

Functional currency must be configured at company level.

## 10. General Ledger Reports

- Journal Register.
- General Ledger.
- Account Statement.
- Trial Balance.
- Detailed Trial Balance.
- Opening Balances.
- Period Movements.
- Closing Balances.
- Cost Center Reports.
- Branch Reports.

## 11. Internal Controls

- Role-based access control.
- Segregation of duties.
- Approval history.
- Posting history.
- Audit trail.
- Prevention of duplicate posting.
- Secure and atomic posting operations.

## 12. Testing Requirements

Test cases must include:

- Balanced and unbalanced entries.
- Multi-currency entries.
- Closed-period posting attempts.
- Approval permissions.
- Duplicate posting attempts.
- Reversal entries.
- Concurrent voucher numbering.
- Automatic journal generation.

No module is production-ready until all relevant accounting and security tests pass.
# Additional General Ledger Requirements

## 1. Configurable Journal Approval Workflow

The system shall support configurable journal approval workflows based on:

- Company and Branch.
- Journal Type.
- Transaction Amount.
- Journal Source.
- User Role and Permissions.
- Account Categories.
- Other configurable business conditions.

Approval workflows shall support multiple approval levels and financial approval limits.

The system shall enforce segregation of duties where required, preventing users from approving their own transactions when the applicable policy prohibits it.

## 2. Journal Numbering Management

The system shall support configurable journal numbering sequences.

Numbering configurations may include:

- Company.
- Fiscal Year.
- Journal Type.
- Document Prefix.
- Sequence Number.

Journal numbers must remain unique within their defined scope.

The numbering mechanism must safely handle concurrent transactions and prevent duplicate numbers.

## 3. Accounting Period Management

The system shall support the following accounting period statuses:

- Open.
- Soft Closed.
- Hard Closed.

The system shall provide configurable restrictions for each status.

Reopening a closed period shall require appropriate authorization and shall be recorded in the audit trail.

Posting dates and transaction dates shall be validated against the applicable fiscal year and accounting period.

## 4. Journal Sources and Automatic Posting

The General Ledger shall support manual and automatically generated journals from integrated modules, including:

- Sales.
- Procurement.
- Accounts Receivable.
- Accounts Payable.
- Inventory.
- Treasury and Banking.
- Import Management.
- Fixed Assets.
- Manufacturing.
- Human Resources and Payroll.
- Foreign Exchange Revaluation.
- Intercompany Transactions.

Each automatically generated journal must retain its original source module, transaction reference, and supporting document references.

The system shall prevent duplicate journal generation from the same source transaction.

## 5. Journal Status and Lifecycle Management

The system shall support configurable journal lifecycle statuses, including:

- Draft.
- Submitted.
- Approved.
- Rejected.
- Posted.
- Reversed.

The required workflow may vary according to journal type and company configuration.

All status changes shall be recorded with the responsible user, date, time, and relevant comments.

## 6. Journal Validation Rules

Before posting, the system shall validate:

- Total debit equals total credit in the functional currency.
- All accounts are active and allow posting.
- The accounting period is open.
- Required analytical dimensions are provided.
- Currency and exchange rate information is valid.
- Company and branch access is authorized.
- Required approvals have been completed.
- The source transaction has not already been posted.
- All mandatory journal information is available.

Invalid journals must not be posted.

## 7. Posted Journal Protection

Posted journals shall be immutable.

The system shall not allow direct modification or deletion of posted journal headers or lines.

Corrections shall be processed through:

- Reversal Journals.
- Adjustment Journals.
- Linked Correction Transactions.

The original journal must remain available for audit purposes, with a clear reference to the related correction or reversal.

## 8. Multi-Currency Journal Processing

The journal structure shall support:

- Transaction Currency.
- Functional Currency.
- Exchange Rate.
- Exchange Rate Date.
- Foreign Currency Debit and Credit.
- Functional Currency Debit and Credit.
- Currency Precision.
- Rounding Differences.

The system shall calculate foreign currency differences according to the applicable accounting rules.

Historical exchange rates used in posted transactions must remain preserved.

## 9. Atomic Journal Posting and Concurrency Control

Journal posting shall be executed within an atomic database transaction.

The system must ensure that:

- Either the complete journal is posted successfully or no posting takes place.
- Partial journal posting is not permitted.
- Concurrent posting requests are safely controlled.
- Duplicate posting requests are rejected or handled idempotently.
- Failed posting operations are rolled back.
- Journal numbering remains unique under concurrent processing.

## 10. General Ledger Reporting

The General Ledger shall provide configurable reports, including:

- Journal Register.
- General Ledger.
- Account Statement.
- Trial Balance.
- Detailed Trial Balance.
- Opening Balance, Period Movements, and Closing Balance.
- Cost Center Reports.
- Department Reports.
- Branch Reports.
- Project Reports.
- Multi-Currency Account Statements.
- Posted and Unposted Journal Reports.

Reports shall support filtering by tenant, company, branch, fiscal year, period, account, currency, journal type, source, and status, subject to user permissions.

## 11. Audit Trail and Posting History

The system shall maintain a complete history of journal activities, including:

- Journal Creation.
- Journal Modification before posting.
- Submission.
- Approval and Rejection.
- Posting.
- Reversal.
- Period Reopening.
- Changes to journal configurations.

The audit trail shall identify the user, timestamp, action, and relevant record references.

## 12. General Ledger Integration and Reconciliation

The General Ledger shall provide reconciliation capabilities with integrated subledger modules.

These shall include:

- Accounts Receivable to GL Reconciliation.
- Accounts Payable to GL Reconciliation.
- Inventory to GL Reconciliation.
- Fixed Assets to GL Reconciliation.
- Payroll to GL Reconciliation.
- Treasury and Bank to GL Reconciliation.
- Intercompany Balance Reconciliation.

Reconciliation reports shall identify differences and provide references to the underlying transactions.

## 13. General Ledger Testing Requirements

Testing shall cover:

- Balanced and unbalanced journals.
- Multi-currency journals.
- Exchange rate differences.
- Closed accounting periods.
- Approval workflow restrictions.
- Segregation of duties.
- Duplicate journal prevention.
- Journal reversal and adjustment.
- Concurrent journal numbering.
- Atomic posting and rollback.
- Automatic journals from integrated modules.
- Subledger-to-GL reconciliation.
- Audit trail completeness.
