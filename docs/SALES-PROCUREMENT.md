# Sales, Procurement & Import Management
## Smart ERP – Functional Design Specification

### 1. Objective

The module manages the complete sales and procurement cycles, including local purchasing, foreign purchasing, import operations, inventory integration, invoicing, and financial accounting.

The system shall support configurable workflows, approvals, document tracking, and automatic integration with the General Ledger.

### 2. Sales Management

#### 2.1 Sales Cycle

The system shall support the following workflow:

1. Customer Inquiry
2. Sales Quotation
3. Sales Order
4. Credit and Availability Check
5. Stock Reservation
6. Delivery Note
7. Sales Invoice
8. Customer Collection
9. Sales Return

#### 2.2 Sales Features

- Multiple quotation versions.
- Configurable price lists.
- Customer-specific prices and discounts.
- Discount approval limits.
- Partial order fulfillment.
- Partial deliveries.
- Backorders for outstanding quantities.
- Sales representatives and commissions.
- Customer credit limit validation.
- Sales order cancellation with authorization.
- Complete document history.

### 3. Procurement Management

#### 3.1 Procurement Cycle

The system shall support:

1. Purchase Requisition (PR)
2. Requisition Approval
3. Request for Quotation (RFQ)
4. Supplier Quotations
5. Quotation Comparison
6. Supplier Selection
7. Purchase Order (PO)
8. Goods Receipt Note (GRN)
9. Purchase Invoice
10. Supplier Payment
11. Purchase Return

#### 3.2 Procurement Features

- Multiple supplier quotations.
- Supplier quotation comparison.
- Purchase price history.
- Purchase orders with multiple items.
- Partial deliveries and receipts.
- Outstanding purchase order tracking.
- Purchase approval workflows.
- Purchase budget controls.
- Supplier performance evaluation.
- Local and foreign purchasing.
- Document attachment management.

### 4. Import Management

The system shall provide a dedicated Import Management module connected to Procurement, Inventory, Banking, and General Ledger.

#### 4.1 Import File

Each import operation shall have a unique Import File Number and include:

- Company and Branch.
- Foreign Supplier.
- Purchase Order Reference.
- Proforma Invoice.
- Commercial Invoice.
- Currency.
- Exchange Rate.
- Country of Origin.
- Port of Loading.
- Port of Arrival.
- Shipping Method.
- Incoterms.
- Expected Shipment Date.
- Expected Arrival Date.
- Actual Arrival Date.
- Import Status.

#### 4.2 Letters of Credit (LC)

The system shall support tracking of:

- LC Application.
- Issuing Bank.
- LC Number.
- LC Opening Date.
- LC Currency and Amount.
- Beneficiary.
- Expiry Date.
- Shipment Deadline.
- LC Amendments.
- Bank Charges.
- Documents Presented.
- LC Settlement and Closure.

The system shall maintain a complete history of LC amendments and related banking transactions.

#### 4.3 Import Banking Procedures

The system shall support configurable tracking of:

- Import Form 4 (نموذج 4).
- Bank Import Documents.
- Foreign Currency Transfers.
- Advance Payments.
- LC Payments.
- Collection Documents.
- Bank Correspondence.
- Bank Charges.
- Payment Confirmations.

Regulatory and banking requirements shall be configurable by country and effective date.

#### 4.4 Shipping Documents

The system shall track:

- Commercial Invoice.
- Packing List.
- Bill of Lading.
- Certificate of Origin.
- Insurance Certificate.
- Shipping Documents.
- Customs Declaration.
- Customs Release Documents.
- Other Supporting Documents.

Each document shall have an attachment, reference number, issue date, and status where applicable.

### 5. Import Expenses and Landed Cost

The system shall calculate the final landed cost of imported goods.

Supported expenses include:

- International Freight.
- Marine Insurance.
- Customs Duties.
- Customs Clearance.
- Port Charges.
- Transportation.
- Bank Charges.
- Inspection Fees.
- Other Import Expenses.

#### 5.1 Cost Allocation Methods

Expenses shall be allocated using configurable methods:

- Quantity.
- Weight.
- Volume.
- Item Value.
- Equal Allocation.
- Manual Allocation.

Different expense types may use different allocation methods.

#### 5.2 Landed Cost Calculation

The system shall calculate:

- Purchase Cost.
- Allocated Import Expenses.
- Total Landed Cost.
- Landed Cost per Item.
- Landed Cost per Unit.

The system shall support actual and estimated expenses, with later adjustments when final invoices are received.

Tax amounts recoverable under applicable tax rules shall be treated separately from inventory cost where appropriate.

### 6. Inventory Integration

The system shall integrate sales, procurement, and import operations with Inventory Management.

Features include:

- Stock reservation for sales orders.
- Goods receipt against purchase orders.
- Partial goods receipt.
- Inspection and quality control.
- Rejected and damaged quantities.
- Warehouse transfers.
- Batch and serial number tracking.
- Inventory costing integration.
- Import shipment tracking.
- Automatic stock updates after authorized receipt.

### 7. Pricing and Discounts

The system shall support:

- Multiple sales price lists.
- Customer-specific pricing.
- Supplier purchase prices.
- Quantity-based discounts.
- Percentage and fixed discounts.
- Promotional pricing.
- Multi-currency prices.
- Effective dates.
- Approval rules for exceptional discounts.

### 8. Document Workflow and Statuses

All documents shall have configurable workflow statuses.

Examples:

**Sales Quotation:** Draft, Submitted, Approved, Sent, Accepted, Rejected, Expired.

**Sales Order:** Draft, Submitted, Approved, Partially Delivered, Delivered, Closed, Cancelled.

**Purchase Order:** Draft, Submitted, Approved, Partially Received, Received, Closed, Cancelled.

**Import File:** Open, Documents Pending, LC Opened, Shipped, In Transit, Arrived, Customs Clearance, Received, Cost Finalized, Closed.

These statuses may be customized according to company requirements.

### 9. General Ledger Integration

The module shall generate accounting entries based on approved and posted transactions.

Examples:

**Sales Invoice**
- Debit: Accounts Receivable.
- Credit: Sales Revenue.
- Credit: Output Tax Payable, where applicable.

**Goods Delivery**
- Debit: Cost of Goods Sold.
- Credit: Inventory.

**Purchase Receipt**
- Debit: Inventory / Goods Received Not Invoiced.
- Credit: Goods Received Not Invoiced / Inventory Receipt Clearing, according to the configured accounting policy.

**Supplier Invoice**
- Debit: Goods Received Not Invoiced / Inventory / Expense.
- Debit: Recoverable Input Tax, where applicable.
- Credit: Accounts Payable.

**Import Expense Capitalized into Inventory**
- Debit: Inventory.
- Credit: Accounts Payable / Bank / Expense Clearing.

Accounting treatment shall depend on the transaction type and configured accounting policy. The system must prevent duplicate posting.

### 10. Multi-Currency and Exchange Rates

The module shall support:

- Foreign purchase currencies.
- Multiple exchange rates.
- Transaction date exchange rates.
- Settlement exchange differences.
- Import expense currency conversion.
- Actual versus estimated exchange rates.
- Configurable exchange rate sources.
- Exchange rate audit history.

### 11. Reports and Dashboards

#### Sales Reports
- Sales Analysis.
- Sales by Customer.
- Sales by Item.
- Sales Order Status.
- Pending Deliveries.
- Sales Returns.
- Gross Profit Analysis.

#### Procurement Reports
- Purchase Analysis.
- Purchase by Supplier.
- Purchase Price Comparison.
- Outstanding Purchase Orders.
- Pending Goods Receipts.
- Supplier Performance.

#### Import Reports
- Import Shipment Status.
- Open Import Files.
- LC Status and Expiry.
- Import Expenses.
- Estimated versus Actual Import Cost.
- Landed Cost per Item.
- Import Payment Schedule.
- Import Operations Summary.

### 12. Security and Audit Trail

The system shall support:

- Role-based permissions.
- Multi-level approvals.
- Document-level access controls.
- Financial approval limits.
- Audit trail for all changes.
- Document attachments.
- Cancellation and reversal history.
- Segregation of duties.

Posted transactions shall not be directly deleted or modified.

### 13. Testing Requirements

The module must be tested for:

- Complete sales cycle.
- Complete procurement cycle.
- Partial sales deliveries.
- Partial purchase receipts.
- Multiple supplier quotations.
- Purchase approval workflows.
- Customer credit limit restrictions.
- Import files with multiple currencies.
- LC amendments and payment tracking.
- Import document tracking.
- Multiple landed cost allocation methods.
- Estimated versus actual import expenses.
- Inventory costing updates.
- Duplicate accounting posting prevention.
- Audit trail completeness.
