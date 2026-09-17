# Budget vs Actual — Payroll Variance Analysis

An Excel / Power Query project that compares **budgeted payroll costs against actual payroll spend** across five departments (Finance, HR, IT, Operations, Sales) for Q1 2026 (Jan–Mar), using raw employee, payroll, and attendance data.

## 📌 Project Overview

Most organizations set a monthly payroll budget per department, but actual spend depends on real-world factors — attendance, overtime, bonuses, and deductions. This project builds an end-to-end workflow that:

1. Ingests raw HR data (employee master, daily attendance logs, payroll transactions)
2. Cleans and joins it with Power Query
3. Rolls it up into actual monthly net pay by department
4. Compares it against the department's monthly budget
5. Surfaces the variance in a pivot table for quick review

## 🗂️ Data Sources

| Source | Description |
|---|---|
| `Employee Master` | 40 employees — ID, name, department, designation, branch, date of joining, employment type, base salary |
| `Payroll_Raw` | Monthly payroll transactions — basic pay, allowance, deduction, bonus, and computed net pay per employee |
| `Attendance_Jan`, `Feb attendance`, `Master attendance` | Daily time-in/time-out logs with hours worked and status (Present / Half Day / Absent / On Leave) |
| `Sheet1` | Monthly budgeted payroll figures per department |

## ⚙️ Workflow

- **Power Query merges** (`Merge1`, `Merge2`) join attendance and payroll records to the Employee Master on `EmployeeID`, pulling in department, designation, and branch.
- Payroll records are aggregated to **Total Net Pay by Department and Month**.
- Actual totals are compared against the budget (`Sheet1`) to compute **Variance = Actual − Budget**.
- A **pivot table** (`Budget VS Actual`) summarizes the variance by department, by month, with a grand total.

## 📊 Key Findings (Jan–Mar 2026)

- Overall actual payroll spend came in **~₹1.48M under budget** across the quarter.
- **HR was the only department over budget** every month (+₹130K total variance) — actual pay consistently exceeded what was planned.
- **IT showed the largest underspend** (−₹784K), followed by Sales (−₹501K) and Operations (−₹320K).
- Finance stayed closest to budget, with a small net variance of −₹4.9K.
- Attendance data shows the workforce was largely present (~85% of logged days), with absences and leave accounting for the rest — a useful cross-check against payroll deductions.

*(Figures are illustrative of the dataset's structure — replace with your own headline numbers if the data changes.)*

## 🛠️ Tools Used

- **Microsoft Excel**
- **Power Query** — data cleaning, joins, and transformation
- **Pivot Tables** — variance summarization and reporting

## 📁 Repository Structure

```
├── Budget_VS_Actual.xlsx     # Main workbook (raw data + Power Query + pivot output)
└── README.md                 # Project documentation
```

## 🚀 How to Use

1. Clone or download this repository.
2. Open `Budget_VS_Actual.xlsx` in Excel.
3. Refresh the Power Query connections (Data → Refresh All) if you update the raw data sheets.
4. Review the `Budget VS Actual` pivot table for the latest variance summary.

## 📈 Possible Next Steps

- Add a Power BI / dashboard layer for interactive filtering by department or month.
- Extend the analysis with headcount and overtime trends.
- Automate monthly refresh with Power Automate or a scheduled script.

