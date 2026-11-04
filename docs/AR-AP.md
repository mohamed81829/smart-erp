# Accounts Receivable & Accounts Payable (AR/AP)
## Smart ERP – Functional Design Specification

### 1. Objective
The AR/AP module manages customer and supplier transactions, outstanding balances, invoices, collections, payments, credit notes, debit notes, and settlement processes.

The module must integrate automatically with the General Ledger (GL).

### 2. Business Partner Master Data

The system shall maintain one unified Business Partner record.

Each Business Partner may have one or both roles:
- Customer
- Supplier

Required information:
- Unique Business Partner ID
- Business Partner Code
- Arabic and English Names
- Tax Registration Number
- Commercial Registration Number
- Address and Contact Details
- Country
- Currency
- Payment Terms
- Credit Limit
- Active/Inactive Status

The same Business Partner may have different customer and supplier settings.

### 3. Accounts Receivable (Customers)

The system shall support:
- Sales invoices
- Cash sales
- Credit sales
- Sales returns
- Credit notes
- Debit notes
- Customer receipts
- Partial collections
- Advance receipts
- Customer balance adjustments

### 4. Accounts Payable (Suppliers)

The system shall support:
- Purchase invoices
- Cash purchases
- Credit purchases
- Purchase returns
- Supplier credit notes
- Supplier debit notes
- Supplier payments
- Partial payments
- Advance payments
- Supplier balance adjustments

### 5. Invoice Management

Each invoice shall include:
- Invoice Number
- Invoice Date
- Due Date
- Company and Branch
- Business Partner
- Currency
- Exchange Rate
- Payment Terms
- Subtotal
- Discount
- Tax
- Total Amount
- Outstanding Amount
- Reference Number
- Invoice Status

The system shall support configurable tax rules and multiple currencies.

### 6. Collections and Payments

The system shall support:
- Cash
- Bank Transfers
- Cheques
- Other configurable payment methods

Payment functionality:
- Full payment
- Partial payment
- One payment allocated to multiple invoices
- Multiple payments allocated to one invoice
- Unallocated advances
- Payment allocation and reallocation
- Payment cancellation with proper authorization and audit trail

### 7. Accounts Aging

The system shall calculate outstanding balances based on invoice due dates.

Default aging periods:
- Not Due
- 1–30 Days
- 31–60 Days
- 61–90 Days
- More than 90 Days

Aging periods must be configurable.

Reports shall include:
- Customer Aging
- Supplier Aging
- Outstanding Invoices
- Due and Overdue Invoices
- Customer Statements
- Supplier Statements

### 8. Credit Management

The system shall support:
- Customer credit limits
- Payment terms
- Credit exposure monitoring
- Overdue balance monitoring
- Configurable warnings and transaction restrictions
- Authorized credit limit overrides

### 9. General Ledger Integration

All approved and posted AR/AP transactions shall generate corresponding GL entries automatically.

Examples:

**Credit Sales Invoice**
- Debit: Accounts Receivable
- Credit: Sales Revenue
- Credit: Output Tax Payable

**Customer Receipt**
- Debit: Bank / Cash
- Credit: Accounts Receivable

**Purchase Invoice**
- Debit: Inventory / Expense
- Debit: Input Tax Receivable, where applicable
- Credit: Accounts Payable

**Supplier Payment**
- Debit: Accounts Payable
- Credit: Bank / Cash

The system must prevent duplicate GL posting.

### 10. Multi-Currency

The module shall support:
- Transaction Currency
- Functional Currency
- Exchange Rates
- Realized Exchange Differences
- Unrealized Exchange Differences
- Foreign Currency Revaluation
- Configurable rounding rules

### 11. Intercompany Transactions

A company within a group may act as a customer or supplier of another company.

The system shall support:
- Intercompany invoices
- Intercompany balances
- Reciprocal account mapping
- Intercompany reconciliation
- Consolidation elimination references

### 12. Tax Configuration

Tax rules shall be configurable by:
- Company
- Transaction Type
- Tax Category
- Effective Date
- Tax Rate

Tax rules must not be permanently hardcoded, allowing future legal and regulatory changes.

### 13. Security and Audit Trail

The system shall maintain:
- Role-based permissions
- Invoice approval workflows
- Payment approval workflows
- User activity logs
- Modification history
- Cancellation and reversal history
- Segregation of duties

Posted financial transactions must not be directly deleted or modified. Corrections shall be performed through authorized reversal or adjustment transactions.

### 14. Required Reports

- Customer Balance Summary
- Supplier Balance Summary
- Customer Account Statement
- Supplier Account Statement
- AR Aging
- AP Aging
- Collection Report
- Payment Report
- Outstanding Invoices
- Overdue Invoices
- Advance Payments
- Unallocated Receipts and Payments
- Customer and Supplier Ledger
- Intercompany Reconciliation

### 15. Testing Requirements

The module must be tested for:
- Cash and credit invoices
- Partial collections and payments
- Multiple invoice allocation
- Returns and credit notes
- Debit notes
- Foreign currency transactions
- Exchange differences
- Credit limit restrictions
- Overdue invoice calculations
- Duplicate GL posting prevention
- Intercompany transactions
- Transaction cancellation and reversal
- Audit trail completeness
