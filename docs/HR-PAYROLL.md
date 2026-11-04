# Human Resources & Payroll Management
## Smart ERP – Functional Design Specification

### 1. Objective

The HR & Payroll module manages employee records, organizational structures, attendance, leave, payroll calculations, employee benefits, loans, deductions, and employee settlements.

The module shall integrate with Treasury, Cost Centers, and General Ledger.

It shall support multiple countries, starting with Egypt.

### 2. Employee Master Data

Each employee shall have a unique Employee ID.

Employee information shall include:

- Employee Code.
- Arabic and English Name.
- Contact Information.
- Nationality.
- Country.
- Employment Date.
- Contract Type.
- Job Title.
- Department.
- Branch.
- Cost Center.
- Direct Manager.
- Basic Salary.
- Payment Method.
- Bank Account Details.
- Employment Status.

Sensitive employee information shall be protected through role-based permissions.

### 3. Organizational Structure

The system shall support:

- Companies.
- Branches.
- Departments.
- Sections.
- Job Positions.
- Grades and Salary Levels.
- Reporting Hierarchies.
- Cost Center Assignments.

Organizational structures shall be configurable for each company.

### 4. Recruitment and Onboarding

The system shall support:

- Job Requisitions.
- Candidate Records.
- Recruitment Stages.
- Interview Records.
- Job Offers.
- Employee Onboarding.
- Required Documents.
- Employment Contract Records.

Recruitment features may be activated separately from core payroll functions.

### 5. Attendance and Time Management

The system shall support:

- Daily Attendance.
- Check-In and Check-Out.
- Late Arrivals.
- Early Departures.
- Absence Tracking.
- Overtime.
- Shift Management.
- Flexible Working Hours.
- Attendance Corrections.
- Attendance Approval.

The system shall support integration with biometric attendance devices and external attendance systems where available.

### 6. Leave Management

The system shall support configurable leave types:

- Annual Leave.
- Sick Leave.
- Emergency Leave.
- Unpaid Leave.
- Maternity and Other Statutory Leave.
- Other Company-Specific Leave Types.

Features:
- Leave Entitlements.
- Opening Balances.
- Leave Accrual.
- Leave Requests.
- Approval Workflows.
- Leave Balance Calculation.
- Leave Carry Forward.
- Leave Settlement.

Leave rules shall be configurable by country and company policy.

### 7. Payroll Management

The payroll engine shall support:

**Earnings**
- Basic Salary.
- Housing Allowance.
- Transportation Allowance.
- Meal Allowance.
- Overtime.
- Incentives.
- Bonuses.
- Commissions.
- Other Allowances.

**Deductions**
- Income Tax.
- Social Insurance.
- Employee Loans.
- Salary Advances.
- Absence Deductions.
- Penalties, where legally permitted.
- Other Authorized Deductions.

Payroll components shall be configurable by company, employee category, and country.

### 8. Multi-Country Payroll Engine

The system shall support country-specific payroll rules.

Each country configuration shall include:

- Income Tax Rules.
- Social Insurance Rules.
- Employer Contributions.
- Employee Contributions.
- Tax Exemptions.
- Allowance Treatment.
- Statutory Deductions.
- Payroll Periods.
- Minimum and Maximum Limits.
- Effective Dates.

The initial country configuration shall be Egypt.

The system shall not hardcode tax rates, insurance rates, exemptions, or statutory limits into the payroll calculation engine.

All legal parameters shall be maintained in effective-dated configuration tables with version history and authorized updates.

The system shall support future country configurations without changing the core payroll architecture.

### 9. Egypt Payroll Configuration

The Egypt configuration shall support:

- Egyptian Income Tax Calculations.
- Social Insurance Calculations.
- Employer and Employee Contributions.
- Applicable Tax Exemptions.
- Applicable Insurance Wage Limits.
- Monthly Payroll.
- Payroll Tax Reports.
- Social Insurance Reports.
- Statutory Payroll Adjustments.

All rates, thresholds, exemptions, and calculation rules shall be maintained according to the applicable legislation and effective dates.

The system shall support historical recalculation for authorized corrections while retaining previous payroll results.

### 10. Loans and Salary Advances

The system shall support:

- Employee Loans.
- Salary Advances.
- Loan Approval.
- Repayment Schedules.
- Monthly Installments.
- Outstanding Balances.
- Early Settlement.
- Loan Adjustments.

Each transaction shall be linked to the employee account.

### 11. Payroll Processing Workflow

The payroll cycle shall include:

1. Attendance Collection.
2. Attendance Validation.
3. Variable Earnings and Deductions.
4. Payroll Calculation.
5. Payroll Review.
6. Payroll Approval.
7. Payroll Posting.
8. Salary Payment.
9. Payroll Reports and Payslips.

Payroll periods shall support monthly and other configurable frequencies.

### 12. Employee Benefits and End of Service

The system shall support:

- Employee Benefits.
- Medical Benefits.
- Insurance Benefits.
- Leave Encashment.
- End-of-Service Settlements.
- Resignation.
- Termination.
- Final Salary Calculation.
- Outstanding Loans and Advances.
- Final Settlement Approval.

Legal entitlements shall be calculated according to applicable country rules and effective dates.

### 13. Employee Self-Service Portal

The system shall optionally provide an employee portal for:

- Viewing Payslips.
- Checking Leave Balances.
- Submitting Leave Requests.
- Viewing Attendance.
- Updating Permitted Personal Information.
- Requesting Salary Advances.
- Downloading Employment Documents.

Employee access shall be restricted to their own authorized information.

### 14. Payroll Accounting Integration

Approved payroll transactions shall generate automatic GL entries.

**Payroll Recognition**
- Debit: Salary Expense.
- Debit: Allowances Expense.
- Debit: Employer Social Insurance Expense.
- Credit: Net Salaries Payable.
- Credit: Income Tax Payable.
- Credit: Social Insurance Payable.
- Credit: Other Payroll Liabilities.

**Salary Payment**
- Debit: Net Salaries Payable.
- Credit: Bank Account.

**Employee Loan or Advance**
- Debit: Employee Loans / Advances.
- Credit: Bank / Cash.

Accounting mappings shall be configurable by payroll component, company, branch, and cost center.

### 15. Reports and Dashboards

- Employee Master Report.
- Employee Movement Report.
- Organizational Structure.
- Attendance Report.
- Absence Report.
- Overtime Report.
- Leave Balances.
- Payroll Summary.
- Payroll Register.
- Employee Payslips.
- Tax Report.
- Social Insurance Report.
- Employer Contributions.
- Employee Loan Report.
- End-of-Service Settlement.
- Payroll Cost by Department.
- Payroll Cost by Cost Center.

### 16. Security and Audit Trail

The module shall support:

- Role-Based Access Control.
- Confidential Salary Permissions.
- Payroll Approval Workflows.
- Employee Data Permissions.
- Separation of HR and Payroll Responsibilities.
- Complete Salary Change History.
- Payroll Calculation History.
- User Activity Logs.
- Secure Payslip Access.

Approved payroll records shall not be directly modified or deleted.

### 17. Testing Requirements

The module must be tested for:

- Employee Creation and Updates.
- Multiple Companies and Branches.
- Attendance Calculations.
- Overtime Calculations.
- Leave Accrual.
- Payroll Earnings and Deductions.
- Egypt Tax Configuration.
- Social Insurance Calculations.
- Effective-Dated Legal Changes.
- Employee Loans and Advances.
- Payroll Approval.
- Salary Payment.
- End-of-Service Settlement.
- Cost Center Allocation.
- Automatic GL Posting.
- Employee Data Security.
- Audit Trail Completeness.
