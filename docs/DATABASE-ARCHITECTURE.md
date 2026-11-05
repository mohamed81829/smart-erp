# Database Architecture

## 1. Database Technology
The system will use **PostgreSQL** as its primary relational database management system (RDBMS).

PostgreSQL is selected for its reliability, data integrity, security, scalability, transaction management, and support for complex financial operations.

## 2. Multi-Tenant Database Architecture
The system will follow a **Shared Database + Shared Schema** architecture.

- All tenants will initially use one shared PostgreSQL database.
- All tenants will use the same database schema and tables.
- Each tenant's data will be identified using a unique `Tenant ID`.
- Every tenant-owned record must be linked to its corresponding `Tenant ID`.
- The system must enforce strict tenant data isolation.
- Users must never be able to access data belonging to another tenant without explicit authorized access.

## 3. Organizational Structure
The database must support the following organizational hierarchy:

- Platform
- Tenant
- Group
- Company
- Branch

Each level must have clearly defined relationships and access permissions.

## 4. Multi-Company Support
The database must support:

- Multiple groups under one tenant.
- Multiple companies within each group.
- Multiple branches within each company.
- Independent accounting records for each company.
- Consolidated financial reporting at group level.
- Intercompany transactions between companies.

## 5. Database Security and Data Integrity
The database architecture must support:

- Strict tenant-level data isolation.
- Company and branch-level access restrictions.
- Role-based access control.
- Referential integrity and foreign key constraints.
- Secure transaction handling.
- Audit trails for important data changes.
- Backup and recovery procedures.

Tenant isolation must be enforced at the database and application levels, not only through the user interface.

## 6. Future Database Scalability
The initial architecture will use a shared database and shared schema.

However, the system should be designed to support dedicated databases for selected large tenants in the future, without requiring a complete redesign of the application.

## 7. Database Design Principles
The database must follow these principles:

- Normalized relational database design.
- Consistent naming conventions.
- Unique primary keys.
- Appropriate foreign keys and indexes.
- Efficient query performance.
- Accurate handling of financial amounts and decimal precision.
- Support for multiple currencies.
- Effective date management for configurable business rules.
- Data consistency and transactional integrity.
# Additional Database Architecture Requirements

## 1. Multi-Tenant Database Structure

The database shall use a shared database and shared schema architecture, with strict logical separation between tenants.

The following organizational hierarchy shall be supported:

- Platform: Central platform administration.
- Tenant: The subscribed customer or organization.
- Group: A group of related companies.
- Company: An independent legal and accounting entity.
- Branch: An operational branch belonging to a company.

Each tenant-owned record must be associated with the appropriate Tenant ID.

Records belonging to companies, branches, and groups must also maintain the relevant organizational references.

Platform-level reference data may be maintained separately where appropriate.

## 2. Tenant Data Isolation

Tenant isolation shall be enforced at the database and application levels.

The database design shall support:

- Tenant ID in all tenant-owned tables.
- Tenant-aware primary and unique constraints.
- Composite foreign keys where required to prevent cross-tenant relationships.
- Validation of tenant ownership when creating or updating relationships.
- Company and branch scope validation.
- PostgreSQL Row-Level Security (RLS) as an additional security layer where appropriate.
- Tenant context validation in background jobs and scheduled operations.

A record belonging to one tenant must never reference a record belonging to another tenant unless an explicitly authorized platform-level integration is designed for that purpose.

Tenant isolation must be verified through automated database and application security tests.

## 3. Primary Keys and Data Integrity

The database shall use consistent primary key and relationship conventions.

The following principles shall apply:

- Use globally unique identifiers, preferably UUIDs, for primary keys where appropriate.
- Define foreign key constraints for related records.
- Use composite unique constraints where uniqueness is tenant-specific.
- Prevent orphan records.
- Define appropriate deletion and update rules for relationships.
- Use database constraints to enforce critical business rules wherever practical.

Document numbers and business codes shall be handled separately from internal database identifiers.

## 4. Standard Audit Fields

Business tables shall include standard audit fields where applicable:

- Created At.
- Created By.
- Updated At.
- Updated By.
- Tenant ID.
- Company ID, where applicable.
- Branch ID, where applicable.

Financial and operational transactions shall additionally maintain relevant approval, posting, cancellation, and reversal references.

Audit information must not be silently overwritten or removed.

## 5. Soft Delete and Historical Data Protection

The database shall support controlled record deactivation and deletion.

The following rules shall apply:

- Master data may use soft deletion or inactive status where appropriate.
- Records referenced by posted transactions must not be physically deleted.
- Posted financial and inventory transactions must remain preserved.
- Corrections must be handled through controlled reversal or adjustment transactions.
- Historical records must remain available for audit and reporting.
- Any permitted deletion must be subject to authorization and audit logging.

Retention and archival policies shall be configurable according to legal and business requirements.

## 6. Database Indexing and Performance

Database indexes shall be designed according to actual application queries and reporting requirements.

Important indexing considerations include:

- Tenant ID.
- Company ID.
- Branch ID.
- Transaction Date.
- Posting Date.
- Document Number.
- Account ID.
- Customer and Supplier IDs.
- Item ID.
- Warehouse ID.
- Transaction Status.
- Foreign key columns.

Composite indexes shall be created where frequently used filters and joins require them.

Indexing must be reviewed periodically to avoid unnecessary indexes and performance overhead.

Large transaction tables may require partitioning when transaction volumes justify it.

## 7. Financial Data Types and Precision

Financial values must use appropriate fixed-precision decimal database types.

Floating-point data types must not be used for financial calculations.

The database shall support:

- Debit and Credit Amounts.
- Transaction Currency Amounts.
- Functional Currency Amounts.
- Exchange Rates.
- Tax Amounts.
- Unit Costs.
- Inventory Values.
- Quantity Precision.
- Rounding Rules.

Currency precision and rounding rules shall be configurable according to the relevant currency and accounting requirements.

Calculations must preserve sufficient precision before applying final rounding rules.

## 8. Multi-Currency Data Structure

The database shall support multi-currency transactions.

Relevant transaction records shall maintain, where applicable:

- Transaction Currency.
- Functional Currency.
- Exchange Rate.
- Transaction Currency Amount.
- Functional Currency Amount.
- Exchange Rate Date.
- Exchange Rate Type or Source.
- Currency Precision.

Historical exchange rates must be preserved and must not be changed retroactively when new rates are entered.

The system shall support realized and unrealized foreign exchange differences through the appropriate accounting processes.

## 9. Effective-Dated Configuration and Historical Rules

Business configurations that may change over time shall support effective dates and historical versions.

Examples include:

- Tax Rates.
- Social Insurance Rules.
- Exchange Rate Configurations.
- Approval Limits.
- Depreciation Policies.
- Accounting Policies.
- Payroll Rules.
- Document Numbering Rules.
- Pricing and Discount Rules.

The database shall maintain:

- Effective From Date.
- Effective To Date, where applicable.
- Version or Revision Number.
- Created By.
- Approved By, where required.
- Change History.

Historical transactions must retain the rules and values applicable when they were processed.

## 10. Transaction Management and Concurrency

The database shall support reliable transaction processing and data consistency.

The following controls shall be implemented:

- ACID transactions.
- Appropriate transaction isolation levels.
- Row-level locking where required.
- Safe handling of simultaneous updates.
- Atomic financial posting.
- Atomic inventory movements.
- Duplicate transaction prevention.
- Rollback on failed operations.
- Idempotency for operations that may be retried.

Critical operations such as journal posting, payment processing, and inventory transfers must not leave partially completed records.

Document numbering must remain unique and reliable under concurrent processing.

## 11. Financial Ledger and Transaction History

The database shall preserve detailed transaction history for financial and operational records.

The design shall support:

- Journal Headers and Journal Lines.
- General Ledger Entries.
- Subledger Transactions.
- Customer and Supplier Allocations.
- Inventory Movements.
- Bank Transactions.
- Fixed Asset Transactions.
- Payroll Transactions.
- Manufacturing Transactions.
- Intercompany Transactions.

Posted records must remain traceable to their original source documents.

Financial balances and reports must be reproducible from the underlying transaction records.

Any stored summary balances must be reconcilable with the underlying transaction details.

## 12. Database Migration and Version Control

Database structure changes shall be managed through controlled migrations.

The migration process shall support:

- Version-controlled database changes.
- Migration history.
- Controlled schema updates.
- Data migration and transformation.
- Rollback procedures where technically safe.
- Migration testing before production deployment.

Database changes must be reviewed to ensure compatibility with existing business data and application modules.

## 13. Backup, Recovery, and Data Retention

The database architecture shall support:

- Automated backups.
- Point-in-Time Recovery where available.
- Encrypted backup storage.
- Configurable retention policies.
- Database restoration procedures.
- Periodic recovery testing.
- Documented disaster recovery procedures.

Backup and recovery processes must preserve tenant data integrity and organizational relationships.

## 14. Database Security

Database access shall follow the principle of least privilege.

The following controls shall be implemented:

- Restricted database user permissions.
- Separate application and administrative access.
- Secure credential management.
- Encrypted database connections.
- Protection of sensitive employee and financial information.
- Controlled access to backups.
- Secure handling of database logs.
- No direct database access from the frontend.

Sensitive data shall be protected according to its classification and applicable legal requirements.

## 15. Database Testing and Validation

The database architecture shall be tested for:

- Tenant isolation.
- Cross-tenant relationship prevention.
- Company and branch data consistency.
- Foreign key integrity.
- Unique document numbering.
- Concurrent transaction processing.
- Financial decimal precision.
- Multi-currency calculations.
- Historical data preservation.
- Database migration integrity.
- Backup restoration.
- Performance under large transaction volumes.

The database shall not be considered production-ready until critical integrity, security, and recovery tests have been successfully completed.
