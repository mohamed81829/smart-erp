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
