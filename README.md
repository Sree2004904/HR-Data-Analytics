# HR-Data-Analytics
HR Data Analytics dashboard in Power BI — tracks headcount, salary, gender mix, join trends, and leave balance with clean drill-downs by job title. Includes dataset, data dictionary, and screenshot. Open HR Data Analytics and refresh with your data.
# HR Data Analytics — Power BI



A practical HR Analytics dashboard built in Power BI using a clean star‑style model. It answers day‑to‑day People Ops questions—headcount, salary distributions, gender mix, join trends, and leave balance health—with simple drill‑downs by job title, department, location, and more.

> File to open: HR Data Analytics.pbix (Power BI Desktop).  
> Dataset: hr-data.xlsx.  
> Screenshot: Dashboard image.png

---

## ✨ What’s Inside

- KPI Cards: Headcount, Avg Salary, Avg Leave Balance, and Count of employees with high leave balance (>20 days).  
- Breakdowns:  
  - Headcount by Job Title (bar)  
  - Gender mix (pie)  
  - Age distribution by gender (histogram)  
  - Salary vs Qualification (scatter)  
  - Headcount & Cumulative Headcount by Date of Join (line)  
  - Avg Leave Balance & >20 days by Job Title (bar)  
  - Controls: Job Title slicers for quick focus.

---

## 📊 Quick KPIs (from the current dataset)

- Headcount: 161
- Average Salary: 54,231.06
- Average Leave Balance: 16.42
- Leave Balance > 20 days (count): 29
- Gender Split (unique employees): {'Female': 88, 'Male': 73}



---

## 🗂 Repository Structure


.
├── HR Data Analytics.pbix
├── hr-data.xlsx
├── dasboard image 
├── README.md
└── 
    └── overview.png


---

## 🧱 Data Notes

- The dataset is provided as Excel (hr-data.xlsx). A data dictionary is generated at data_dictionary.csv with column names, dtypes and null counts.  
- Personally identifiable information should be anonymized before publishing.

### Data Dictionary Preview
(see the full data_dictionary.csv in the repo)

| column | dtype | non_null | nulls | example |
|---|---|---|---|---|
| Name | object | 161 | 0 | 'Barr Faughny' |
| Emp ID | object | 161 | 0 | 'AC0001' |
| Gender | object | 161 | 0 | 'Male' |
| Education Qualification | object | 161 | 0 | "Bachelor's Degree" |
| Date of Join | datetime64[ns] | 161 | 0 | Timestamp('2020-06-12 00:00:00') |
| Job Title | object | 161 | 0 | 'Chocolatier' |
| Salary | int64 | 161 | 0 | 51300 |
| Age | float64 | 161 | 0 | 26.0 |
| Leave Balance | int64 | 161 | 0 | 13 |


---

## ▶ Getting Started

1. Open HR Data Analytics.pbix in Power BI Desktop (May 2024 or newer recommended).  
2. In Transform Data, set your data source or keep hr-data.xlsx.  
3. Refresh and explore the pages—use slicers to drill by Job Title/Department.

---

## 🧮 Measures (DAX Sketch)

DAX
Headcount := DISTINCTCOUNT('Employees'[EmployeeID])

Avg Salary := AVERAGE('Employees'[Salary])

Avg Leave Balance := AVERAGE('Employees'[LeaveBalance])

Leave Balance > 20 (Count) :=
CALCULATE(
    COUNTROWS('Employees'),
    'Employees'[LeaveBalance] > 20
)

Cumulative Headcount by DoJ :=
CALCULATE(
    DISTINCTCOUNT('Employees'[EmployeeID]),
    FILTER(ALL('Date'[Date]), 'Date'[Date] <= MAX('Date'[Date]))
)




---

## 📸 Screenshots

- dasboard image 

---

## 🧠 Insights 

- Early signals on high leave balance pockets by role.  
- Clear view of gender mix and age cohorts.  
- Hiring velocity visible via cumulative Date of Join trends.  
- Salary vs Qualification helps spot pay alignment.
