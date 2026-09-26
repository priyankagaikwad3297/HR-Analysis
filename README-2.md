# HR Analytics Dashboard – Power BI

An interactive one-page HR Analytics dashboard built in **Power BI**, focused on employee headcount, attrition, demographics, salary bands, and job-role satisfaction.

## 📊 Overview

The dashboard gives HR/management a single view to answer:
- How many employees are active vs. total, and what is the attrition rate?
- Which departments, salary slabs, and job roles lose the most people?
- How does attrition vary by age group, gender, and experience?
- What does the department-wise headcount split look like?

## 🗂️ Data Source

- File: `HR_Analytics-4.csv`
- ~1,480 employee records, 37 columns

Key columns used in this dashboard:

| Category | Columns |
|---|---|
| Identity | `EmpID`, `EmployeeNumber` |
| Demographics | `Age`, `AgeGroup`, `Gender`, `MaritalStatus`, `Education`, `EducationField` |
| Job details | `Department`, `JobRole`, `JobLevel`, `BusinessTravel`, `OverTime` |
| Compensation | `MonthlyIncome`, `SalarySlab`, `DailyRate`, `HourlyRate`, `SalaryHike %` |
| Experience | `TotalExperience(Years)`, `YearsatCompany`, `YearsinCurrentRole`, `YearsSincePromotion`, `YearsWithCurrManager`, `NumCompaniesWorked` |
| Satisfaction | `JobSatisfaction`, `EnvironmentSatisfaction`, `RelationshipSatisfaction`, `WorkLifeBalance`, `JobInvolvement`, `PerformanceRating` |
| Target | `Attrition` (Yes/No) |

## 🧹 Data Preparation (Power Query)

1. Imported the CSV into Power BI Desktop (`Get Data → Text/CSV`).
2. Verified column data types (numeric fields for `Age`, `MonthlyIncome`, experience/tenure columns; text for categorical fields).
3. Checked for and removed duplicate/blank `EmpID` rows.
4. Confirmed `Attrition` as a binary Yes/No field to drive all attrition visuals.
5. Kept `AgeGroup` and `SalarySlab` as pre-binned categorical fields (18-25, 26-35, 36-45, 46-55, 55+ and 0-3 LPA, 3-6 LPA, 6-10 LPA, 10+ LPA) for quick slicing.
6. Loaded the cleaned table into the data model for visual creation.

## 📐 Key Measures (DAX)

- **Total Employee** – total employee count
- **Active Employee** – count where `Attrition = "No"`
- **Attrition Count** – count where `Attrition = "Yes"`
- **Attrition Rate %** – `Attrition Count / Total Employee`
- **Average Age** – average of `Age`
- **Avg Experience** – average of `TotalExperience(Years)`

## 📈 Dashboard Layout

**Top strip – KPI cards**
- Total Employee, Active Employee, Attrition Count, Attrition Rate %, Average Age, Avg Experience
- `AgeGroup` slicer (18-25 / 26-35 / 36-45 / 46-55 / 55+) for filtering the whole page

**Left panel**
- `Department` slicer (button-style list): Administration, Finance, Human Resources, IT, Marketing, Operations, Sales

**Main visuals**
| Visual | Type | Shows |
|---|---|---|
| Attrition by Department | Donut chart | Share of attrition per department |
| Attrition by SalarySlab | Stacked bar chart | Attrition Yes/No count across salary bands |
| Attrition by Job Role & Satisfaction | Matrix | Job satisfaction level (1–4) × job role, with row totals |
| Age Group Distribution | Column chart | Headcount per age bucket |
| Attrition by Gender | Pie chart | Male vs Female attrition split |
| Attrition Trend by Experience | Area chart | Attrition pattern across years of experience |
| Department-Wise Employee Count | Funnel chart | Headcount ranked by department |

## 🛠️ Tools Used

- Power BI Desktop
- Power Query (data cleaning/shaping)
- DAX (KPI measures)
- Visuals: Card, Donut, Stacked Bar, Matrix, Column, Pie, Area, Funnel

## 🔑 Key Insights

- Overall attrition rate sits around **16%**.
- The **Sales** and **Administration** departments contribute the largest share of attrition.
- Employees in the **0–3 LPA** and **3–6 LPA** salary slabs show the highest attrition counts.
- Attrition is concentrated in the **26–35** and **36–45** age groups, and drops off sharply after **10 years of experience**.
- **Laboratory Technician** and **Sales Representative/Executive** roles report the most low-satisfaction (level 1–2) responses.

## 🚀 How to Use

1. Open the `.pbix` file in Power BI Desktop.
2. Use the **Department** panel and **AgeGroup** slicer at the top to filter all visuals at once.
3. Hover over any chart for tooltips with exact counts and percentages.
4. Click a department name or bar to cross-filter the rest of the page.

## 📁 Files

- `HR_Analytics-4.csv` – raw dataset
- `HR_Analytics_DASHBOARD.pbix` – Power BI dashboard file
