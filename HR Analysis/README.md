# HR Analytics -- Power BI Project

An end-to-end **HR Analytics dashboard built using Microsoft Power BI**
to analyze workforce composition, employee attrition, engagement,
compensation, promotion, retrenchment, and employee risk indicators.

The project transforms employee-level HR data into interactive reports
that can help HR teams understand workforce patterns, identify areas
requiring attention, and support data-informed workforce planning.

------------------------------------------------------------------------

## Project Overview

Human Resources teams need a clear view of employee data to understand
workforce composition and monitor important indicators such as
attrition, satisfaction, compensation, and career progression.

This project uses Power BI to build an interactive HR analytics solution
from the supplied Excel workbook. It covers data preparation, data
modeling, calculated columns, DAX measures, dashboard development, and
business-focused analysis.

**Primary audience:** HR leadership, HR business partners, and workforce
planning teams.

## Business Objectives

-   Understand workforce distribution across departments, job roles, job
    levels, and demographics.
-   Analyze employee attrition and identify segments with comparatively
    higher attrition.
-   Explore employee engagement and satisfaction indicators.
-   Review compensation patterns across departments, roles, and job
    levels.
-   Analyze employees due for promotion and employees flagged for
    retrenchment.
-   Create a rule-based employee risk score to prioritize further HR
    review.
-   Present findings through interactive dashboards and employee-level
    details.

## Tools & Technologies

  -----------------------------------------------------------------------
  Tool / Technology                   Purpose
  ----------------------------------- -----------------------------------
  Microsoft Excel                     Source data

  Power BI Desktop                    Data modeling, DAX, visualizations,
                                      and dashboard development

  Power Query                         Data cleaning and transformation

  DAX                                 Calculated columns and KPI measures

  GitHub                              Project documentation and portfolio
                                      presentation
  -----------------------------------------------------------------------

## Dataset

**Source file:** `HR Analytics Data.xlsx`

The workbook contains four sheets:

  Sheet            Records (as specified in the project BRD) Purpose
  -------------- ------------------------------------------- --------------------------------------------------
  HR                                                   1,470 Main employee-level dataset containing 35 fields
  Employees                                            1,470 Employee number/name mapping
  Promotion                                               72 Employees identified as due for promotion
  Retrenchment                                         1,470 Retrenchment status information

The HR sheet is the primary analytical source. `EmployeeNumber` is the
employee identifier and the intended grain is one row per employee.

### Main Data Categories

-   **Employee and demographics:** Age, Gender, Education, Marital
    Status
-   **Organization:** Department, Job Role, Job Level, Business Travel
-   **Attrition and work conditions:** Attrition, OverTime, Distance
    From Home
-   **Engagement:** Job Satisfaction, Environment Satisfaction,
    Relationship Satisfaction, Work-Life Balance, Job Involvement
-   **Compensation:** Monthly Income, Daily Rate, Hourly Rate, Monthly
    Rate
-   **Career and tenure:** Total Working Years, Years At Company, Years
    In Current Role, Years Since Last Promotion
-   **Workforce actions:** Promotion and Retrenchment flags

> The source workbook is not necessarily included in this repository.
> Add it only if you have permission to share the data. Do not publish
> confidential or personally identifiable employee information.

## Data Preparation

The project follows these data preparation steps in Power Query:

1.  Load all four Excel sheets.
2.  Review column names and assign appropriate data types.
3.  Clean text fields by trimming whitespace and standardizing values.
4.  Check missing values, duplicates, and unexpected categories.
5.  Standardize employee identifiers before matching related sheets.
6.  Merge employee information and match promotion/retrenchment records
    using available identifiers.
7.  Create promotion and retrenchment flags.
8.  Create business-friendly categories such as Age Band, Salary Band,
    Tenure Band, and Distance Band.
9.  Validate row counts and investigate unmatched records after merges.

## Data Model

The recommended model is an employee-centric analytical table with one
row per employee.

It combines the HR attributes with employee name and the relevant
promotion and retrenchment flags. If source tables are retained
separately, relationships should be designed carefully to avoid
ambiguous many-to-many relationships.

**Project workflow:**

`Excel → Power Query → Clean Employee Data → Data Model → Calculated Columns → DAX Measures → Power BI Reports → Business Insights`

## Key KPIs

The project defines the following business measures:

  KPI                                Definition
  ---------------------------------- ------------------------------------------------
  Total Employees                    Distinct count of EmployeeNumber
  Attrition Employees                Employees where Attrition = Yes
  Attrition Rate                     Attrition Employees ÷ Total Employees × 100
  Retention Employees                Total Employees − Attrition Employees
  Retention Rate                     Retention Employees ÷ Total Employees × 100
  Promotion Due                      Distinct employees flagged for promotion
  Promotion Rate                     Promotion Due ÷ Total Employees × 100
  Retrenchment Employees             Distinct employees flagged for retrenchment
  Retrenchment Rate                  Retrenchment Employees ÷ Total Employees × 100
  Promotion--Retrenchment Conflict   Employees flagged for both actions
  Average Monthly Income             Average Monthly Income across employees
  Median Monthly Income              Median Monthly Income across employees
  Average Age                        Average employee age
  Average Tenure                     Average Years At Company
  Overtime %                         Overtime Employees ÷ Total Employees × 100
  Average Satisfaction               Average satisfaction ratings
  High Risk Employees                Employees with a risk score of 3 or more
  High Risk %                        High Risk Employees ÷ Total Employees × 100

All employee-count measures should use distinct employee identifiers
where appropriate. Percentage measures should respect the selected
report filter context.

## Calculated Columns & Risk Analysis

The project includes business-oriented calculated columns:

-   **Age Band:** Groups employees into age categories.
-   **Salary Band:** Groups employees by monthly income.
-   **Tenure Band:** Groups employees by years at the company.
-   **Distance Band:** Groups employees by distance from home.
-   **Promotion Flag:** 1 when an employee is due for promotion;
    otherwise 0.
-   **Retrenchment Flag:** 1 when an employee is flagged for
    retrenchment; otherwise 0.
-   **Attrition Flag:** 1 when Attrition = Yes; otherwise 0.
-   **Employee Risk Score:** A rule-based score using selected
    indicators such as overtime, low job satisfaction, low environment
    satisfaction, low work-life balance, and frequent business travel.
-   **Risk Category:** Low, Medium, High, or Critical based on the
    score.
-   **Promotion--Retrenchment Conflict:** Identifies employees with both
    action flags.

The proposed risk categories are:

    Risk Score Risk Category
  ------------ ---------------
          0--1 Low
             2 Medium
          3--4 High
             5 Critical

The risk score is an analytical prioritization indicator, not a
predictive model or an automated employment decision tool.

## Power BI Report Pages

The project requirements define six analytical report pages:

  -----------------------------------------------------------------------
  Page                    Report Name             Purpose
  ----------------------- ----------------------- -----------------------
  1                       HR Executive Dashboard  Management overview of
                                                  workforce KPIs,
                                                  attrition, promotion,
                                                  and retrenchment

  2                       Attrition Analysis      Analyze attrition by
                                                  department, role, age,
                                                  job level, overtime,
                                                  travel, and tenure

  3                       Employee Engagement     Explore job,
                                                  environment,
                                                  relationship, and
                                                  work-life satisfaction

  4                       Workforce &             Analyze workforce
                          Compensation            structure, income,
                                                  salary bands, and
                                                  experience

  5                       Promotion &             Review workforce action
                          Retrenchment            flags and identify
                                                  overlapping cases

  6                       HR Risk & Employee      Examine risk
                          Detail                  distribution, employee
                                                  details, and exceptions
  -----------------------------------------------------------------------

### Suggested Interactive Features

-   Slicers for Department, Job Role, Job Level, Gender, Age Band,
    Marital Status, Business Travel, OverTime, and satisfaction.
-   KPI cards for important workforce measures.
-   Charts for department-wise and role-wise comparisons.
-   Matrix and heatmap analysis for workforce segmentation.
-   Employee-level detail table.
-   Drill-through to an Employee Detail page.

## Business Questions

The dashboard is designed to investigate questions such as:

1.  How is the workforce distributed across departments and job roles?
2.  Which departments and job roles have comparatively higher attrition?
3.  How does attrition differ between employees who work overtime and
    those who do not?
4.  How are age, tenure, and job level associated with attrition?
5.  How do satisfaction ratings vary across employee groups?
6.  How does monthly income differ by department, job role, and job
    level?
7.  How many employees are due for promotion or flagged for
    retrenchment?
8.  Are any employees flagged for both promotion and retrenchment?
9.  Which employee segments have higher rule-based risk scores?
10. Which areas may require further HR investigation?

## Data Quality & Validation

The project includes checks for:

-   HR row count and distinct employee count.
-   Duplicate employee identifiers.
-   Duplicate promotion and retrenchment records.
-   Unmatched employees after merging.
-   Validity of promotion and retrenchment flags.
-   Unexpected values in attrition, overtime, travel, and satisfaction
    fields.
-   Invalid or negative age, income, and tenure values.
-   Logical consistency between career and tenure fields.
-   Reconciliation of Power BI KPI results with independently calculated
    Excel totals.
-   Promotion and retrenchment conflicts requiring validation.

## Important Project Limitations

-   The supplied workbook is a point-in-time employee dataset. It does
    not support genuine monthly or yearly attrition trends without
    additional historical or date-based data.
-   Relationships between variables should be described as associations
    or observed patterns, not proof of causation.
-   Retrenchment and attrition are different concepts. An employee
    flagged for retrenchment should not automatically be counted as an
    attrition employee unless the Attrition field indicates Yes.
-   The rule-based risk score is intended to prioritize analysis and HR
    review. It must not be used to automate promotion, termination, or
    retrenchment decisions.

## Repository Structure

A suggested GitHub repository structure:

``` text
HR-Analytics-PowerBI/
│
├── README.md
├── HR_Analytics.pbix
├── dataset/
│   └── HR Analytics Data.xlsx
├── screenshots/
│   ├── executive_dashboard.png
│   ├── attrition_analysis.png
│   ├── employee_engagement.png
│   ├── workforce_compensation.png
│   ├── promotion_retrenchment.png
│   └── hr_risk_employee_detail.png
└── documentation/
    └── HR_Analytics_PowerBI_Project_BRD.docx
```

This is a suggested structure. Include only files that are actually part
of your repository. If the source dataset contains personal or
confidential information, do not upload it publicly.

## Project Status

This README describes the project scope and requirements from the
Business Requirements Document. Update the report screenshots,
implementation details, and findings after completing and validating the
Power BI report.

## Author

**\[Your Name\]**\
Aspiring Data Analyst \| Power BI \| SQL Server \| Excel \| Python

-   GitHub: [Add your GitHub profile link](https://github.com/)
-   LinkedIn: [Add your LinkedIn profile
    link](https://www.linkedin.com/)

------------------------------------------------------------------------

*Built as an end-to-end HR Analytics portfolio project using Microsoft
Power BI.*
