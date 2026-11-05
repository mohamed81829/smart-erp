# Manufacturing & Production Management
## Smart ERP – Functional Design Specification

### 1. Objective

The Manufacturing module manages production planning, material requirements, production orders, work centers, manufacturing operations, production costs, quality control, and finished goods.

It shall integrate with Inventory, Procurement, Sales, Cost Accounting, and General Ledger.

The system shall support both basic and advanced manufacturing.

### 2. Manufacturing Types

**Basic Manufacturing**
- Simple assembly.
- Raw material consumption.
- Finished goods production.
- Basic production orders.
- Material cost calculation.

**Advanced Manufacturing**
- Multi-stage production.
- Multiple production lines.
- Work centers.
- Routing and operations.
- Capacity planning.
- Work-in-Progress tracking.
- Detailed production costing.
- Quality checkpoints.

Each company shall be able to activate the manufacturing features required for its operations.

### 3. Item and Product Configuration

The system shall support:
- Raw Materials.
- Semi-Finished Goods.
- Finished Goods.
- Components.
- Consumables.
- Packaging Materials.
- By-Products.
- Scrap Materials.

Each item shall be linked to its inventory and accounting settings.

### 4. Bill of Materials (BOM)

The system shall support configurable Bills of Materials.

Each BOM shall include:
- BOM Number.
- Finished Product.
- Component Items.
- Required Quantities.
- Units of Measure.
- Expected Scrap Percentage.
- Expected Yield.
- Effective From and To Dates.
- BOM Version.
- Production Notes.

Features:
- Multi-level BOM.
- Alternative Components.
- BOM Version Control.
- BOM Approval.
- Estimated Material Cost.
- BOM Comparison.

### 5. Production Routing and Work Centers

For advanced manufacturing, the system shall support:

**Work Centers**
- Work Center Code.
- Description.
- Production Line.
- Machine Information.
- Capacity.
- Operating Hours.
- Cost Rate.
- Availability.

**Routing**
- Operation Sequence.
- Operation Description.
- Work Center.
- Setup Time.
- Run Time.
- Labor Requirements.
- Machine Requirements.
- Expected Production Capacity.

### 6. Production Planning

The system shall support:
- Production Plans.
- Master Production Schedule (MPS).
- Material Requirements Planning (MRP).
- Production Forecasts.
- Sales Order Driven Production.
- Make-to-Stock.
- Make-to-Order.
- Capacity Planning.
- Material Availability Checks.

MRP shall calculate:
- Gross Material Requirements.
- Available Inventory.
- Existing Purchase Orders.
- Existing Production Orders.
- Net Material Requirements.
- Suggested Purchase Requisitions.
- Suggested Production Orders.

### 7. Production Orders

Each Production Order shall include:
- Production Order Number.
- Product.
- Planned Quantity.
- Production Quantity.
- BOM Version.
- Routing Reference.
- Planned Start Date.
- Planned Completion Date.
- Actual Start Date.
- Actual Completion Date.
- Production Warehouse.
- Finished Goods Warehouse.
- Production Status.

Supported statuses:
- Draft.
- Planned.
- Approved.
- Released.
- In Progress.
- Partially Completed.
- Completed.
- Closed.
- Cancelled.

### 8. Material Issue and Consumption

The system shall support:
- Material Requisitions.
- Material Reservations.
- Material Issues.
- Partial Material Issues.
- Actual Material Consumption.
- Additional Material Requests.
- Material Returns.
- Scrap Recording.

Material consumption shall be compared with BOM standards.

### 9. Production Execution

The system shall support:
- Production Start.
- Operation Completion.
- Work Center Updates.
- Labor Time Recording.
- Machine Time Recording.
- Production Quantity Recording.
- Partial Production Completion.
- Production Downtime.
- Rework.
- Scrap and Waste Recording.

The system shall track planned versus actual production performance.

### 10. Work in Progress (WIP)

The system shall track production costs accumulated before completion.

WIP may include:
- Raw Material Costs.
- Direct Labor Costs.
- Machine Costs.
- Manufacturing Overhead.
- Other Eligible Production Costs.

The system shall calculate WIP balances by production order and production stage.

### 11. Finished Goods Receipt

The system shall support:
- Finished Goods Receipt.
- Partial Production Receipts.
- Quality Inspection.
- Rejected Quantities.
- Rework Quantities.
- Batch and Serial Number Assignment.
- Finished Goods Warehouse Transfer.

Accepted finished goods shall update inventory automatically.

### 12. Production Costing

The system shall support:
- Standard Costing.
- Actual Costing.
- Direct Material Cost.
- Direct Labor Cost.
- Machine Cost.
- Manufacturing Overhead.
- Subcontracting Cost.
- Scrap and Waste Cost.
- Production Variance Analysis.

The system shall compare actual production cost with standard cost.

### 13. Manufacturing Variances

The system shall calculate configurable variance categories:

- Material Price Variance.
- Material Usage Variance.
- Labor Rate Variance.
- Labor Efficiency Variance.
- Overhead Spending Variance.
- Overhead Efficiency Variance.
- Production Yield Variance.
- Scrap Variance.

Variance reports shall support production orders, products, and cost centers.

### 14. Quality Management

The system shall support:
- Raw Material Inspection.
- In-Process Inspection.
- Finished Goods Inspection.
- Quality Test Plans.
- Acceptance Criteria.
- Rejection Reasons.
- Non-Conformance Reports.
- Corrective Actions.
- Quality Approval.

Quality controls shall be configurable by product and production stage.

### 15. Subcontracting

The system shall support outsourced production operations.

Features:
- Subcontracting Purchase Orders.
- Materials Sent to Subcontractor.
- Materials Consumed.
- Materials Returned.
- Subcontracting Charges.
- Finished or Semi-Finished Goods Receipt.
- Subcontractor Balance Tracking.

### 16. General Ledger Integration

Production transactions shall generate accounting entries automatically.

**Material Issue to Production**
- Debit: Work in Progress.
- Credit: Raw Materials Inventory.

**Direct Labor**
- Debit: Work in Progress.
- Credit: Payroll / Labor Clearing.

**Manufacturing Overhead**
- Debit: Work in Progress.
- Credit: Manufacturing Overhead Applied.

**Finished Goods Receipt**
- Debit: Finished Goods Inventory.
- Credit: Work in Progress.

**Production Variances**
- Recorded in appropriate variance accounts according to configured costing policies.

The system shall prevent duplicate posting and retain links to production orders.

### 17. Reports and Dashboards

- Production Plan Report.
- Production Order Status.
- Material Requirements Report.
- Material Consumption Report.
- BOM Cost Report.
- Work Center Utilization.
- Production Efficiency.
- WIP Report.
- Finished Goods Report.
- Scrap and Waste Report.
- Production Cost Analysis.
- Standard versus Actual Cost.
- Manufacturing Variance Report.
- Quality Inspection Report.
- Subcontracting Report.

### 18. Security and Audit Trail

The module shall support:
- Production Approval Workflows.
- Material Issue Authorization.
- Production Completion Approval.
- Quality Approval.
- Costing Permissions.
- Role-Based Access Control.
- Complete Production History.
- User Activity Logs.

Posted production transactions shall not be directly deleted or modified.

### 19. Testing Requirements

The module must be tested for:
- Basic assembly production.
- Multi-level BOM.
- BOM version changes.
- Production planning.
- MRP calculations.
- Material availability.
- Partial material issues.
- Actual material consumption.
- Multi-stage production.
- Work center capacity.
- WIP calculation.
- Finished goods receipts.
- Production costing.
- Variance calculation.
- Scrap and rework.
- Quality inspections.
- Subcontracting.
- Automatic GL posting.
# Advanced Manufacturing Requirements

## 1. Manufacturing Planning and Production Orders
- Support Make-to-Stock (MTS), Make-to-Order (MTO), and configurable production strategies.
- Support production orders generated manually or from approved sales orders and demand forecasts.
- Maintain production order status, planned quantity, completed quantity, rejected quantity, and remaining quantity.
- Support partial production completion and partial material consumption.
- Allow production order priorities, planned start dates, and expected completion dates.
- Support production order amendments with proper authorization and audit history.

## 2. Bill of Materials (BOM)
- Support multi-level and multi-version Bills of Materials.
- Maintain effective dates and revision history for each BOM.
- Support alternative and substitute materials.
- Allow configurable material quantities, scrap percentages, and expected wastage.
- Support configurable BOM approval workflows.
- Prevent unauthorized changes to BOM versions already used in approved production orders.

## 3. Routings and Work Centers
- Support production routings with multiple operations and work centers.
- Maintain operation sequence, standard setup time, processing time, and expected output.
- Support machine capacity, labor capacity, and work center calendars.
- Track actual versus planned production time.
- Allow alternative routings where applicable.

## 4. Material Planning and Consumption
- Calculate material requirements based on approved production orders and BOM versions.
- Check material availability across warehouses and locations.
- Support material reservations and shortages reporting.
- Generate material requisitions for required components.
- Support material issue, return, and additional consumption.
- Record actual consumption against planned consumption.
- Support lot and serial number traceability where applicable.
- Maintain authorization controls for material substitutions and excess consumption.

## 5. Work in Progress (WIP)
- Track work in progress by production order and operation.
- Record material, labor, machine, and overhead costs accumulated in WIP.
- Support partial production completion and WIP transfers.
- Reconcile WIP balances with production records and the General Ledger.
- Prevent completed production orders from being closed while unresolved quantities or costs remain, unless authorized.

## 6. Production Costing
- Support Standard Costing and Actual Costing.
- Support configurable overhead allocation methods.
- Calculate planned and actual material, labor, machine, and overhead costs.
- Calculate production variances, including:
  - Material Price Variance.
  - Material Usage Variance.
  - Labor Rate Variance.
  - Labor Efficiency Variance.
  - Overhead Spending Variance.
  - Overhead Efficiency and Absorption Variances.
- Support by-product and co-product costing.
- Support scrap and wastage costing.
- Allow configurable cost allocation methods for joint products.
- Maintain production cost history and controlled cost updates.

## 7. Production Execution and Quality
- Record production quantities at each operation.
- Track good output, rejected output, rework, and scrap.
- Support quality inspection at receiving, during production, and at final production stages.
- Maintain configurable inspection criteria and acceptance rules.
- Prevent rejected or unapproved products from being transferred to available finished goods stock.
- Record non-conformance reports and corrective actions.

## 8. Subcontracting and Outsourced Manufacturing
- Support subcontracted production operations.
- Track materials sent to subcontractors and materials consumed or returned.
- Record subcontracting service costs.
- Reconcile materials held by subcontractors.
- Support partial subcontracting receipts and outstanding quantities.
- Integrate subcontracting costs into production cost calculations.

## 9. Production Planning and Capacity
- Support demand forecasting and production planning.
- Calculate required production quantities based on sales demand, available stock, and safety stock.
- Support finite and infinite capacity planning as configurable methods.
- Identify work center overloads and production bottlenecks.
- Provide planned versus actual production schedules.
- Allow production rescheduling with appropriate authorization.

## 10. Manufacturing Accounting Integration
- Integrate production transactions with Inventory and General Ledger.
- Transfer issued raw materials into WIP where applicable.
- Capitalize eligible production costs into finished goods.
- Record production variances and scrap according to configurable accounting policies.
- Support finished goods receipts and WIP clearance.
- Prevent duplicate accounting entries between Manufacturing and Inventory modules.
- Maintain full traceability from source materials to finished products.

## 11. Reporting and Testing
- Provide production order status and progress reports.
- Provide material consumption and variance reports.
- Provide WIP valuation and reconciliation reports.
- Provide production cost and profitability reports.
- Provide work center utilization and capacity reports.
- Provide scrap, rejection, and rework reports.
- Test multi-level BOMs and BOM revisions.
- Test partial material issues and production completions.
- Test material substitutions and excess consumption approvals.
- Test actual versus standard costing and variance calculations.
- Test subcontracting and material traceability.
- Test WIP-to-GL reconciliation and duplicate transaction prevention.
