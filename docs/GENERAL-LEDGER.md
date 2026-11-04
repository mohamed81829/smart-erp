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
