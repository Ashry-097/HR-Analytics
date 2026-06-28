# HR Analytics Dashboard (Power BI)

An end-to-end HR analytics dashboard built in Power BI, covering workforce overview, demographics, performance tracking, and attrition analysis. The model is built on a star schema with one fact table and five dimension tables, with all metrics driven by DAX measures.

## 📊 Dashboard Pages

### 1. Overview
A high-level snapshot of the workforce:
- KPI cards (Total Employees, Active Employees, Inactive Employees, Average Salary)
- **Employee Hiring Trends** – column chart of hires over time
- **Active Employees by Department** – clustered bar chart
- **Active Employees by Department and Job Role** – treemap

### 2. Demographics
A breakdown of the workforce by personal attributes:
- KPI cards (Youngest Employee, Oldest Employee)
- **Employees by Age** – column chart (using an `AgeBins` calculated column)
- **Employees by Age and Gender** – 100% stacked column chart
- **Employees by Marital Status** – donut chart
- Combo chart for additional demographic trends

### 3. Performance Tracker
An employee-level performance review page, filterable by employee via slicer:
- KPI cards (Start Date, Last Review, Next Review — driven by `LastReviewDate` / `NextReviewDate` measures)
- Trend line charts for: Relationship Satisfaction, Environment Satisfaction, Job Satisfaction, Work Life Balance, Self Rating, Manager Rating
- Supporting detail tables

### 4. Attrition
Analysis of employee turnover drivers:
- Attrition Rate KPI card
- **Attrition by Hire Date** – line chart
- **Attrition by Travel Frequency** – combo chart
- **Attrition by Overtime Requirement** – column chart
- **Attrition by Tenure** – column chart

## 🗂️ Data Model

Star schema with 6 tables:

| Table | Type | Purpose |
|---|---|---|
| `FactPerformanceRating` | Fact | Core performance review records |
| `DimEmployee` | Dimension | Employee details (name, department, job role, gender, age, marital status, hire date, overtime, business travel, ethnicity, tenure) |
| `DimDate` | Dimension | Date table for time intelligence |
| `DimRatingLevel` | Dimension | Lookup for self/manager rating levels |
| `DimSatisfiedLevel` | Dimension | Lookup for satisfaction levels (job, environment, relationship, work-life balance) |
| `DimEducationLevel` | Dimension | Lookup for education levels |

### Key DAX Measures
- `TotalEmployees`, `ActiveEmployees`, `InactiveEmployees`
- `% Attrition Rate`, `% Attrition Rate Date`
- `AverageSalary`
- `LastReviewDate`, `NextReviewDate`
- `JobSatisfaction`, `EnvironmentSatisfaction`, `RelationshipSatisfaction`, `WorkLifeBalance`
- `SelfRating`, `ManagerRating`

### Key Calculated Columns
- `AgeBins` (conditional column for age grouping)

## 🛠️ Tools Used
- **Power BI Desktop** – data modeling, DAX, visualization
- **Power Query (M)** – data transformation
- **DAX** – measures and calculated columns

## 📁 Data Source
Dataset provided as part of a DataCamp course exercise.

## 🚀 How to Use
1. Clone this repository
2. Open `HR_Analytics.pbix` in Power BI Desktop
3. Refresh the data model if connected to a live source
4. Explore the four report pages using the page navigator

## 📌 Notes
This project was built as a practical exercise in HR analytics: modeling relationships across multiple dimension tables, writing DAX for date-based and rating-based measures, and designing a multi-page report that tells a clear workforce story (overview → demographics → performance → attrition).
