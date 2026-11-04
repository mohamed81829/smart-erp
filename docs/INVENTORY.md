# Inventory Management
## Smart ERP – Functional Design Specification

### 1. Objective

The Inventory Management module controls inventory operations across companies, branches, and warehouses.

It shall integrate with Sales, Procurement, Import Management, Manufacturing, and General Ledger.

### 2. Item Master Data

The system shall support four item types:

**1. Stock Item**
- Physical item maintained in inventory.
- Quantity and cost tracking.
- Warehouse transactions.

**2. Service**
- Non-stock service.
- No physical inventory quantity.
- Revenue or expense accounting.

**3. Non-Stock Item**
- Purchased for direct consumption or use.
- No regular inventory balance.
- Direct expense or other configured accounting treatment.

**4. Manufactured Item**
- Produced internally from raw materials and components.
- Supports Bills of Materials and production integration.

Each item shall include:

- Unique Item ID.
- Item Code.
- Arabic and English Description.
- Item Type.
- Item Category.
- Brand and Model.
- Base Unit of Measure.
- Alternative Units.
- Barcode.
- Default Warehouse.
- Inventory Account.
- Sales Account.
- Purchase Account.
- Cost of Goods Sold Account.
- Minimum and Maximum Stock.
- Reorder Level.
- Active/Inactive Status.

### 3. Units of Measure

The system shall support:

- Piece.
- Box.
- Carton.
- Kilogram.
- Ton.
- Liter.
- Meter.
- Other configurable units.

Features:
- Multiple units per item.
- Conversion factors.
- Purchase and sales units.
- Decimal quantity support.
- Unit-specific barcodes where required.

### 4. Warehouse Management

The system shall support:

- Multiple warehouses per company.
- Warehouse locations and bins.
- Main and sub-warehouses.
- Branch-specific warehouses.
- Warehouse managers.
- Warehouse access permissions.
- Stock availability by warehouse.
- Warehouse transfers.

Each warehouse shall have a unique code and configurable settings.

### 5. Inventory Transactions

The system shall support:

- Goods Receipt.
- Goods Issue.
- Stock Transfer.
- Purchase Return.
- Sales Return.
- Inventory Adjustment.
- Opening Stock.
- Goods in Transit.
- Damaged Stock.
- Scrap Transactions.
- Stock Reservation.
- Stock Release.

Each transaction shall include a reference document, date, warehouse, item, quantity, unit, cost, and approval status.

### 6. Inventory Valuation Methods

The system shall support three valuation methods.

**A. FIFO – First In, First Out**

- Inventory is valued using the oldest available cost layers first.
- Each receipt creates a cost layer.
- Issues consume available layers in chronological order.
- Remaining layers determine ending inventory value.

**B. Moving Weighted Average**

- Inventory cost is recalculated after each receipt.
- New average cost is calculated using existing inventory value plus receipt value divided by the resulting quantity.
- Issues use the current moving average cost.

**C. Standard Cost**

- Each item has a predefined standard cost.
- Inventory movements use the configured standard cost.
- Purchase and production variances are recorded separately.
- Standard costs may be updated through controlled effective-dated procedures.

The valuation method shall be configurable by company or item category, subject to consistent accounting policies and applicable standards.

Historical inventory transactions must retain their original valuation records.

### 7. Batch, Serial Number and Expiry Tracking

The system shall support optional tracking by item.

**Batch Tracking**
- Batch Number.
- Manufacturing Date.
- Expiry Date.
- Supplier Batch Reference.
- Quantity by Batch.

**Serial Number Tracking**
- Unique Serial Number.
- Purchase Reference.
- Sales Reference.
- Warranty Information.
- Current Location and Status.

**Expiry Management**
- Expiry date monitoring.
- Near-expiry alerts.
- Expired stock reports.
- Configurable issue rules such as FEFO (First Expired, First Out).

### 8. Stock Reservation and Availability

The system shall support:

- Stock reservation against Sales Orders.
- Reservation by warehouse.
- Partial reservation.
- Reservation release.
- Available Quantity calculation.
- On-Hand Quantity.
- Reserved Quantity.
- Available Quantity.
- Expected Incoming Quantity.
- Expected Outgoing Quantity.

The system shall prevent unauthorized negative inventory, subject to configurable exceptions.

### 9. Inventory Counting

The system shall support:

- Full Physical Inventory.
- Cycle Counting.
- Periodic Stock Counts.
- Blind Count.
- Count Sheets.
- Variance Calculation.
- Adjustment Approval.
- Inventory Reconciliation.

Physical count results shall be compared with system balances.

Approved differences shall generate inventory adjustment transactions and corresponding accounting entries.

### 10. Goods in Transit

The system shall track goods moving between warehouses or locations.

Features:
- Transfer Request.
- Transfer Approval.
- Dispatch Confirmation.
- In-Transit Status.
- Goods Receipt Confirmation.
- Partial Transfer Receipt.
- Missing or Damaged Quantity.
- In-Transit Inventory Reports.

### 11. Inventory Costing and Landed Cost

The module shall integrate with Import Management to include allocated import expenses in inventory cost where applicable.

Supported costs include:
- Purchase Price.
- Freight.
- Insurance.
- Customs Duties.
- Clearance Charges.
- Transportation.
- Other Eligible Costs.

The system shall support estimated and actual landed cost adjustments through controlled transactions.

### 12. Replenishment and Stock Control

The system shall support:

- Minimum Stock Level.
- Maximum Stock Level.
- Reorder Point.
- Safety Stock.
- Economic Order Quantity as an optional planning method.
- Reorder Alerts.
- Suggested Purchase Requisitions.
- Stock Shortage Reports.
- Slow-Moving Inventory.
- Non-Moving Inventory.

### 13. General Ledger Integration

Inventory transactions shall generate accounting entries automatically when approved and posted.

Examples:

**Goods Receipt**
- Debit: Inventory.
- Credit: Goods Received Not Invoiced / Receipt Clearing.

**Goods Issue**
- Debit: Expense / Cost of Goods Sold.
- Credit: Inventory.

**Sales Delivery**
- Debit: Cost of Goods Sold.
- Credit: Inventory.

**Inventory Adjustment – Shortage**
- Debit: Inventory Adjustment Expense.
- Credit: Inventory.

**Inventory Adjustment – Surplus**
- Debit: Inventory.
- Credit: Inventory Adjustment Gain.

The exact accounting treatment shall be configurable according to transaction type and accounting policy.

### 14. Reports and Dashboards

- Stock Balance Report.
- Stock Valuation Report.
- Inventory Movement Report.
- Item Ledger.
- Warehouse Balance.
- Batch and Serial Number Reports.
- Expiry Report.
- Reorder Report.
- Slow-Moving Stock.
- Non-Moving Stock.
- Inventory Aging.
- Goods in Transit.
- Physical Count Variance.
- Inventory Adjustment Report.
- Inventory Cost Analysis.

### 15. Security and Audit Trail

The system shall support:

- Role-Based Access Control.
- Warehouse-specific permissions.
- Transaction approval workflows.
- User activity tracking.
- Inventory adjustment authorization.
- Complete transaction history.
- Reversal and cancellation history.

Posted inventory transactions shall not be directly deleted or modified.

### 16. Testing Requirements

The module must be tested for:

- All four item types.
- Multiple units of measure.
- Multiple warehouses.
- Warehouse transfers.
- Partial receipts and issues.
- FIFO valuation.
- Moving Weighted Average valuation.
- Standard Cost valuation.
- Batch and serial tracking.
- Expiry management.
- Stock reservation.
- Negative inventory controls.
- Physical inventory adjustments.
- Goods in Transit.
- Landed Cost integration.
- Automatic GL posting.
- Concurrent inventory transactions.
