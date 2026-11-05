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
