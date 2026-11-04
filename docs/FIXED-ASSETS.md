# Fixed Assets Management
## Smart ERP – Functional Design Specification

### 1. Objective

The Fixed Assets module manages the complete asset lifecycle, from acquisition and capitalization to depreciation, transfer, revaluation, impairment, disposal, and retirement.

The module shall integrate with Procurement, Inventory, General Ledger, and Financial Reporting.

### 2. Asset Master Data

Each asset shall have:

- Unique Asset ID.
- Asset Code.
- Arabic and English Description.
- Asset Category.
- Asset Class.
- Company and Branch.
- Department.
- Cost Center.
- Physical Location.
- Acquisition Date.
- Capitalization Date.
- Original Cost.
- Residual Value.
- Useful Life.
- Depreciation Method.
- Accumulated Depreciation.
- Net Book Value.
- Asset Status.
- Supplier.
- Purchase Invoice Reference.
- Serial Number.
- Warranty Information.

### 3. Asset Categories

The system shall support configurable categories, such as:

- Land.
- Buildings.
- Machinery and Equipment.
- Vehicles.
- Furniture and Fixtures.
- Computers and IT Equipment.
- Office Equipment.
- Leasehold Improvements.
- Other Configurable Categories.

Each category shall have default accounting and depreciation settings.

### 4. Asset Acquisition

Assets may be acquired through:

- Direct Purchase.
- Purchase Order.
- Supplier Invoice.
- Import Operations.
- Internal Construction or Development.
- Capital Work in Progress (CWIP).

The system shall support:
- Capitalization of eligible acquisition costs.
- Additional costs before the asset is ready for use.
- Asset creation from purchase invoices.
- Multiple assets from one invoice.
- One asset acquired through multiple invoices.
- Approval and capitalization workflows.

### 5. Depreciation Methods

The system shall support three depreciation methods.

**A. Straight Line Method**

Depreciation is calculated evenly over the useful life.

Annual Depreciation:

Annual Depreciation = (Cost - Residual Value) / Useful Life

**B. Reducing Balance Method**

Depreciation is calculated using a configured rate applied to the depreciable carrying amount, subject to the residual value and applicable accounting policy.

The system shall support configurable rates and depreciation conventions.

**C. Units of Production Method**

Depreciation is calculated based on actual production or usage compared with estimated total lifetime production or usage.

Depreciation per Unit:

Depreciation per Unit = (Cost - Residual Value) / Estimated Total Units

Period Depreciation:

Period Depreciation = Depreciation per Unit × Actual Period Units

The system shall support monthly, quarterly, and annual depreciation runs.

### 6. Depreciation Configuration

Each asset shall support:

- Depreciation Start Date.
- Depreciation Frequency.
- Useful Life.
- Residual Value.
- Depreciation Method.
- Depreciation Rate, where applicable.
- Depreciation Calendar.
- Depreciation Convention.
- Depreciation Expense Account.
- Accumulated Depreciation Account.

The system shall calculate depreciation automatically and prevent depreciation beyond the depreciable amount.

### 7. Asset Improvements and Additional Costs

The system shall support:
- Capital Improvements.
- Major Replacements.
- Eligible Subsequent Expenditure.
- Asset Componentization.
- Cost Adjustments.
- Changes to Useful Life and Residual Value.

Each adjustment shall have approval and audit history.

### 8. Asset Transfers

The system shall support transfers between:

- Branches.
- Departments.
- Cost Centers.
- Physical Locations.
- Companies, where applicable through controlled intercompany procedures.

Transfer records shall include:
- Transfer Date.
- Previous Location.
- New Location.
- Responsible Employees.
- Approval History.

### 9. Revaluation and Impairment

The system shall support configurable procedures for:

- Asset Revaluation.
- Fair Value Adjustments.
- Impairment Assessment.
- Impairment Loss.
- Reversal of Impairment, where permitted.

The system shall maintain the historical carrying amounts and accounting treatment for each event.

### 10. Capital Work in Progress (CWIP)

The module shall support projects involving assets under construction.

Features:
- CWIP Project.
- Project Costs.
- Supplier Invoices.
- Internal Costs.
- Accumulated Construction Costs.
- Project Completion.
- Asset Capitalization.
- Transfer from CWIP to Fixed Assets.

Depreciation shall start according to the applicable accounting policy and when the asset is available for use.

### 11. Asset Disposal and Retirement

The system shall support:
- Asset Sale.
- Asset Retirement.
- Asset Write-Off.
- Asset Donation.
- Partial Disposal, where applicable.

The system shall calculate:
- Disposal Proceeds.
- Net Book Value.
- Accumulated Depreciation.
- Gain or Loss on Disposal.

All disposal transactions shall require appropriate authorization.

### 12. General Ledger Integration

The module shall generate accounting entries automatically.

**Asset Acquisition**
- Debit: Fixed Assets.
- Credit: Accounts Payable / Bank / CWIP.

**Depreciation**
- Debit: Depreciation Expense.
- Credit: Accumulated Depreciation.

**Asset Disposal**
- Debit: Bank / Accounts Receivable, where applicable.
- Debit: Accumulated Depreciation.
- Credit: Fixed Asset Cost.
- Difference: Gain or Loss on Disposal.

**Impairment**
- Debit: Impairment Loss.
- Credit: Asset / Accumulated Impairment.

Accounting entries shall be configurable by asset category and transaction type.

### 13. Asset Register and Reports

The system shall provide:

- Fixed Asset Register.
- Asset Acquisition Report.
- Depreciation Schedule.
- Monthly Depreciation Report.
- Accumulated Depreciation Report.
- Net Book Value Report.
- Asset Movement Report.
- Asset Transfer Report.
- Asset Disposal Report.
- CWIP Report.
- Revaluation Report.
- Impairment Report.
- Assets by Branch and Department.
- Assets by Cost Center.

### 14. Security and Audit Trail

The module shall support:
- Role-Based Access Control.
- Asset Approval Workflows.
- Depreciation Run Authorization.
- Transfer Approval.
- Disposal Approval.
- Complete Asset History.
- User Activity Logs.
- Reversal and Adjustment History.

Posted depreciation and asset transactions shall not be directly deleted or modified.

### 15. Testing Requirements

The module must be tested for:
- Asset acquisition.
- Multiple assets from one invoice.
- All three depreciation methods.
- Monthly and annual depreciation.
- Residual value limits.
- Changes in useful life.
- Asset improvements.
- Asset transfers.
- Revaluation and impairment.
- CWIP capitalization.
- Asset disposal.
- Automatic GL posting.
- Depreciation recalculation controls.
- Audit trail completeness.
