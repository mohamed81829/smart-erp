# Smart ERP – Chart of Accounts Design
**Version:** 1.0

## 1. Design Decisions

- Flexible hierarchical account coding.
- One unified Group Chart of Accounts.
- Advanced analytical dimensions.
- Arabic and English account names.

## 2. Account Hierarchy

Illustrative account structure:

1 – Assets
2 – Liabilities
3 – Equity
4 – Revenue
5 – Cost of Sales
6 – Expenses
7 – Other Income and Expenses

Account hierarchy must support configurable depth without hardcoded level limits.

## 3. Account Master Data

Each account must contain:

- Unique Account ID.
- Account Code.
- Arabic Name.
- English Name.
- Parent Account.
- Account Category.
- Normal Balance.
- Posting Account Flag.
- Active Status.
- Effective Date.
- Group Account Mapping where applicable.

## 4. Group and Company Accounts

The Group Chart of Accounts is the unified reporting structure.

Company-level accounts may be mapped to the appropriate Group Accounts.

Multiple company accounts may map to one Group Account.

Mappings must be validated for accounting compatibility.

## 5. Analytical Dimensions

The system must support configurable dimensions:

- Branch.
- Department.
- Cost Center.
- Project.
- Business Unit.
- Product Line.

Each dimension must support:

- Unique Code.
- Arabic and English Names.
- Parent Dimension where applicable.
- Active/Inactive Status.
- Effective Dates.

Dimension requirements must be configurable by account and transaction type.

## 6. Accounting Controls

- Posting is allowed only to active posting accounts.
- Parent accounts cannot receive direct postings.
- Account codes must be unique within the group.
- Accounts with posted transactions cannot be deleted.
- Changes to historical accounting classifications must be controlled.
- All changes must be recorded in the audit trail.

## 7. Consolidation Mapping

Each company account must have a valid group reporting mapping.

The system must support:
- Consolidation classifications.
- Intercompany account identification.
- Currency translation.
- Elimination accounts.
- Consolidated reporting.

## 8. Reporting

The system must support:

- Trial Balance by company.
- Group Trial Balance.
- General Ledger.
- Account Statement.
- Cost Center Reports.
- Departmental Reports.
- Project Profitability.
- Consolidated Financial Statements.

## 9. Validation

Account setup and posting rules must be tested before production deployment.
# Additional Chart of Accounts Requirements

## 1. Financial Statement Mapping

Each account shall support mapping to the relevant financial statement category.

The system shall support the following classifications:

- Statement of Financial Position (SFP).
- Profit or Loss (P/L).
- Other Comprehensive Income (OCI).
- Cash Flow Statement.

Each account shall have a configurable financial statement classification.

The mapping shall support financial reporting at both company and group levels.

## 2. Account Type and Classification

Each account shall maintain additional classification attributes, including:

- Account Type.
- Account Category.
- Account Subcategory.
- Normal Balance (Debit or Credit).
- Financial Statement Category.
- Parent Account.
- Posting Level.
- Account Status.

Account types and classifications shall be configurable while maintaining consistency across financial reporting.

## 3. Control Accounts

The system shall support control accounts linked to their respective subledger modules.

Examples include:

- Accounts Receivable Control Account.
- Accounts Payable Control Account.
- Inventory Control Account.
- Fixed Assets Control Account.
- Accumulated Depreciation Control Account.
- VAT Input Control Account.
- VAT Output Control Account.
- Bank Control Accounts.
- GRNI Control Account.

Control accounts shall support automatic postings from their related modules.

Manual posting restrictions shall be configurable to prevent unauthorized direct entries into control accounts.

## 4. Retained Earnings and Year-End Closing

The Chart of Accounts shall support retained earnings and year-end closing processes.

The system shall provide:

- Retained Earnings Account Configuration.
- Profit and Loss Closing Rules.
- Opening Balance Carry Forward.
- Year-End Closing Journals.
- Comparative Financial Reporting.

Year-end closing shall preserve historical transactions and generate controlled closing entries.

## 5. Currency Restrictions

The system shall allow currency restrictions to be configured for individual accounts.

Supported configurations shall include:

- Any Currency.
- Functional Currency Only.
- Specific Allowed Currencies.
- Foreign Currency Required, where applicable.

Currency restrictions must be validated during journal entry and posting.

## 6. Cash Flow Classification

Accounts shall support cash flow classification for indirect and direct cash flow reporting.

The system shall support:

- Operating Activities.
- Investing Activities.
- Financing Activities.
- Non-Cash Transactions.

Cash flow classifications shall be configurable and may require additional transaction-level information for accurate reporting.

## 7. Account Reconciliation

The system shall support reconciliation requirements at account level.

Each account may be configured with:

- Reconciliation Required.
- Reconciliation Frequency.
- Reconciliation Method.
- Reconciliation Responsibility.
- Reconciliation Status.

Examples include bank accounts, customer control accounts, supplier control accounts, and intercompany accounts.

Reconciliation records shall be linked to the relevant transactions and supporting documents.

## 8. Posting Controls

Each account shall support configurable posting controls, including:

- Allow Manual Posting.
- Allow Automatic Posting.
- Posting Restrictions.
- Required Dimensions.
- Allowed Transaction Types.
- Effective From Date.
- Effective To Date, where applicable.

The system shall prevent postings to:

- Inactive accounts.
- Parent accounts that do not allow posting.
- Accounts outside their effective dates.
- Restricted accounts without the required authorization.

## 9. Group and Company Account Mapping

The system shall support a Group Chart of Accounts and company-specific local account structures.

The following capabilities shall be provided:

- Group-level account definitions.
- Company-specific account codes.
- Mapping between local and group accounts.
- Mapping effective dates.
- Multiple local accounts mapped to one group account where appropriate.
- Mapping validation and audit history.

The mapping shall preserve the original company account references for consolidated reporting and audit purposes.

## 10. Account Dimensions and Analytical Requirements

Accounts shall support configurable analytical dimensions, including:

- Branch.
- Department.
- Cost Center.
- Project.
- Business Unit.
- Product Line.

Dimensions may be configured as mandatory, optional, or restricted according to the account and transaction type.

The system shall validate required dimensions before posting.

## 11. Account Master Data and Change History

The account master shall maintain:

- Account ID.
- Account Code.
- Arabic Account Name.
- English Account Name.
- Parent Account.
- Account Level.
- Account Type.
- Normal Balance.
- Posting Flag.
- Account Status.
- Effective Dates.
- Group Account Mapping.
- Financial Statement Mapping.

All important account configuration changes shall be recorded in the audit trail.

Accounts with posted transactions must not be physically deleted.

## 12. Chart of Accounts Validation and Testing

The system shall validate:

- Unique account codes within the appropriate organizational scope.
- Valid parent-child relationships.
- Prevention of circular account hierarchies.
- Correct normal balance settings.
- Valid group account mappings.
- Posting restrictions.
- Currency restrictions.
- Mandatory analytical dimensions.
- Financial statement classifications.
- Control account integration.

Testing shall include account creation, modification, deactivation, posting restrictions, group mapping, year-end closing, and financial statement reporting.
