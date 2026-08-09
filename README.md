# 📊 HR Workforce Analytics & Employee Performance Dashboard
## 📌 Project Overview

The **HR Workforce Analytics & Employee Performance Dashboard** is an end-to-end data analytics project designed to analyze workforce structure, employee performance, productivity, salary, attendance, and employee attrition.

The project transforms raw employee data into a structured analytical solution using **Python, SQL, Statistics, and Power BI**. The objective is to provide HR stakeholders with measurable workforce KPIs, identify patterns associated with employee turnover, compare departments, and support data-driven workforce planning and retention strategies.

## 🎯 Business Problem

Organizations need reliable workforce insights to make informed decisions about employee retention, productivity, performance, and workforce planning. Without structured analytics, it can be difficult to identify:

• Which departments have the largest workforce and highest employee exits

• What factors are associated with employee turnover

• How employee performance varies across departments

• How salary is distributed across the workforce

• Whether overtime, job satisfaction, engagement, and work-life balance differ between active and exited employees

• Which departments demonstrate higher average project completion

This project addresses these requirements through an integrated Python, SQL, statistical analysis, and Power BI workflow.
## 🎯 Project Objectives

The project was developed to:

1. Clean and preprocess employee data

2. Perform exploratory data analysis (EDA)

3. Analyze workforce composition and departmental trends

4. Analyze employee performance and productivity

5. Analyze employee attrition and retention

6. Analyze salary distribution

7. Analyze attendance and working-hour patterns

8. Calculate key HR KPIs

9. Identify factors associated with employee turnover

10. Perform statistical analysis using an independent two-sample t-test

11. Develop interactive Power BI dashboards

12. Generate actionable HR recommendations

## 📁 Dataset Overview

The raw dataset contains **10,050 employee records and 29 features** covering:

• Employee demographics

• Department and job role

• Location

• Employment type

• Joining and exit dates

• Years at company

• Total work experience

• Education

• Salary

• Performance rating

• Job satisfaction

• Work-life balance

• Monthly and overtime hours

• Attendance

• Projects completed

• Training hours

• Promotions

• Sick days

• Manager rating

• Employee engagement

• Attrition

• Attrition reason

• Remote-work status

After duplicate removal, the analysis dataset contains **10,047 records**.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| **Python** | Data cleaning, preprocessing, EDA, KPI calculation and analysis |
| **Pandas** | Data manipulation and transformation |
| **NumPy** | Numerical analysis |
| **Matplotlib** | Data visualization |
| **Seaborn** | Statistical and exploratory visualizations |
| **SQL / SQLite** | Workforce analysis and HR KPI queries |
| **Jupyter Notebook** | Integrated analysis environment |
| **Power BI** | Interactive dashboard and visualization |
| **Statistics / SciPy** | Statistical comparison and hypothesis testing |
| **Git & GitHub** | Version control and project submission |

## 🔄 Project Workflow

Raw Employee Data
↓
Data Cleaning & Validation
↓
Data Transformation
↓
Exploratory Data Analysis
↓
HR KPI Calculation
↓
Employee Turnover Analysis
↓
Statistical Analysis
↓
SQL Analysis
↓
Power BI Dashboard
↓
Insights & Recommendations

## 1️. Data Preparation

The employee dataset was cleaned and prepared using **Python and Pandas**.

### **Data Preparation Steps**

* Imported the raw CSV dataset
* Inspected dataset dimensions and column data types
* Checked duplicate records
* Checked missing values
* Removed duplicate rows
* Handled missing categorical values using the mode
* Handled missing numerical values using the median
* Converted `Joining_Date` and `Exit_Date` into datetime format
* Validated categorical values
* Reviewed numerical value distributions
* Prepared the final analysis-ready dataset
* Loaded the cleaned data into SQLite for SQL analysis

### **Duplicate Handling**

The raw dataset contained:

* **3 fully duplicated rows**
* **50 duplicate Employee_ID values**

The duplicate records were removed using Pandas `drop_duplicates()`.

### **Missing-Value Treatment**

Missing values were identified in:

* `Exit_Date`
* `Education_Level`
* `Job_Satisfaction`
* `Attendance_Percentage`
* `Training_Hours`
* `Manager_Rating`

`Education_Level` was imputed using the mode, while numerical fields such as job satisfaction, attendance, training hours, and manager rating were imputed using their median values.

`Exit_Date` was converted using `pd.to_datetime(..., errors="coerce")` so that missing or invalid exit dates could be represented safely.

## 2️. Exploratory Data Analysis

EDA was performed to understand workforce characteristics and identify patterns across major HR dimensions.

### **Employee Performance**

The overall employee performance score is based on the average `Performance_Rating`.

* **Overall performance score:** 3.51 / 5
* **Marketing and IT** have the highest department-level average performance rating at approximately 3.52

### **Workforce Distribution**

The workforce is distributed across six departments:

| **Department** | **Employees** |
| -------------- | ------------: |
| IT             |     2,684     |
| Sales          |     2,042     |
| Operations     |     1,909     |
| Finance        |     1,230     |
| Marketing      |     1,201     |
| HR             |       981     |

**IT is the largest department by employee count.**

### **Salary Analysis**

The overall average salary is approximately:

**1,393,347.24**

Average salary by department:

| **Department** | **Average Salary** |
| -------------- | -----------------: |
| IT             |   1,555,932.05     |
| Finance        |   1,448,104.95     |
| Marketing      |   1,341,667.62     |
| Sales          |   1,337,171.92     |
| Operations     |   1,280,940.13     |
| HR             |   1,278,803.71     |

**IT has the highest average salary among the departments.**

### **Attrition Analysis**

The cleaned analytical dataset contains:

* **9,619 active employees**
* **428 exited employees**
* **4.26% attrition rate**
* **95.74% retention rate**

The dashboard shows **Better Opportunity** as the leading recorded attrition reason, followed by **Work-Life Balance**.

### **Department Attrition**

The highest number of employee exits is observed in **IT**, followed by **Sales** and **Operations**. This is influenced partly by the larger workforce size in these departments, so exit counts should be interpreted together with department-level attrition rates.

### **Department Productivity**

Productivity is measured using average `Projects_Completed` per department.

| **Department** | **Average Projects Completed** |
| -------------- | -----------------------------: |
| Marketing      |                       5.25     |
| IT             |                       5.23     |
| Finance        |                       5.23     |
| Operations     |                       5.20     |
| Sales          |                       5.19     |
| HR*            |                       5.07     |

**Marketing records the highest average project completion.**

## 3️. HR Key Performance Indicators

| **KPI**                       |        **Value** |
| ----------------------------- | ---------------: |
| Total Employees               |        10,047    |
| Active Employees              |         9,619    |
| Exited Employees              |           428    |
| Employee Retention Rate       |        95.74%    |
| Employee Attrition Rate       |         4.26%    |
| Average Salary                |  1,393,347.24    |
| Overall Performance Score     |      3.51 / 5    |

### **KPI Definitions**

* **Retention Rate:** Percentage of employees with `Attrition = No`.
* **Attrition Rate:** Percentage of employees with `Attrition = Yes`.
* **Average Salary:** Mean salary across employees.
* **Performance Score:** Mean employee `Performance_Rating`.
* **Department Productivity:** Average `Projects_Completed` by department.

## 4️. Employee Turnover Analysis

The analysis compared active and exited employees across key workforce factors.

| **Factor**              | **Active Employees** | **Exited Employees** |
| ----------------------- | -------------------: | -------------------: |
| Job Satisfaction        |             3.42     |             2.52     |
| Overtime Hours          |            13.59     |            17.55     |
| Salary                  |        1,394,687     |        1,363,229     |
| Employee Engagement     |             3.47     |             2.68     |
| Work-Life Balance       |             3.43     |             2.92     |

The comparison indicates that exited employees have:

* Lower average job satisfaction
* Higher average overtime hours
* Lower average employee engagement
* Lower average work-life balance

These differences provide useful indicators for HR retention strategies.

## 5️. Statistical Analysis

An **independent two-sample t-test** was performed to compare active and exited employees across key numerical factors.

### **Results**

| **Factor**              | **t-statistic** | **p-value** | **Result**                |
| ----------------------- | --------------: | ----------: | ------------------------- |
| Job Satisfaction        |      17.105     | < 0.001     | Significant               |
| Overtime Hours          |      -7.356     | < 0.001     | Significant               |
| Salary                  |       1.959     |  0.0507     | Not significant at 5%     |
| Employee Engagement     |      18.847     | < 0.001     | Significant               |
| Work-Life Balance       |       9.731     | < 0.001     | Significant               |

At the **5% significance level**, Job Satisfaction, Overtime Hours, Employee Engagement, and Work-Life Balance show statistically significant differences between active and exited employees.

Salary has a p-value of **0.0507**, so it is not considered statistically significant at the 5% threshold.

> **Statistical association does not by itself establish causation. The results indicate differences in this dataset and should be interpreted alongside business context.**

## 6️. SQL Analysis

SQL analysis was performed within the Jupyter Notebook using **SQLite**. The cleaned employee dataset was loaded into an SQLite database, and SQL queries were executed to calculate workforce KPIs and analyze departments, salary, performance, productivity, and attrition.

### **6.1 Total Employee Count**

```sql
SELECT COUNT(*) AS total_employees
FROM employees;
```

### **6.2 Active and Exited Employees**

```sql
SELECT
    Attrition,
    COUNT(*) AS employee_count
FROM employees
GROUP BY Attrition;
```

### **6.3 Employee Count by Department**

```sql
SELECT
    Department,
    COUNT(*) AS employee_count
FROM employees
GROUP BY Department
ORDER BY employee_count DESC;
```

### **6.4 Average Salary by Department**

```sql
SELECT
    Department,
    ROUND(AVG(Salary), 2) AS average_salary
FROM employees
GROUP BY Department
ORDER BY average_salary DESC;
```

### **6.5 Average Performance Rating by Department**

```sql
SELECT
    Department,
    ROUND(AVG(Performance_Rating), 2) AS average_performance
FROM employees
GROUP BY Department
ORDER BY average_performance DESC;
```

### **6.6 Attrition by Department**

```sql
SELECT
    Department,
    Attrition,
    COUNT(*) AS employee_count
FROM employees
GROUP BY Department, Attrition
ORDER BY Department, Attrition;
```

### **6.7 Average Overtime Hours by Attrition**

```sql
SELECT
    Attrition,
    ROUND(AVG(Overtime_Hours), 2) AS average_overtime_hours
FROM employees
GROUP BY Attrition;
```

### **6.8 Average Job Satisfaction by Attrition**

```sql
SELECT
    Attrition,
    ROUND(AVG(Job_Satisfaction), 2) AS average_job_satisfaction
FROM employees
GROUP BY Attrition;
```

### **6.9 Department Productivity**

```sql
SELECT
    Department,
    ROUND(AVG(Projects_Completed), 2) AS average_projects_completed
FROM employees
GROUP BY Department
ORDER BY average_projects_completed DESC;
```

### **6.10 Average Employee Engagement by Attrition**

```sql
SELECT
    Attrition,
    ROUND(AVG(Employee_Engagement), 2) AS average_engagement
FROM employees
GROUP BY Attrition;
```

### **6.11 Average Work-Life Balance by Attrition**

```sql
SELECT
    Attrition,
    ROUND(AVG(Work_Life_Balance), 2) AS average_work_life_balance
FROM employees
GROUP BY Attrition;
```

### **6.12 Attrition Rate**

```sql
SELECT
    ROUND(
        100.0 * SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END)
        / COUNT(*),
        2
    ) AS attrition_rate
FROM employees;
```

### **6.13 Retention Rate**

```sql
SELECT
    ROUND(
        100.0 * SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END)
        / COUNT(*),
        2
    ) AS retention_rate
FROM employees;
```

## 7️. Power BI Dashboard

Two Power BI dashboard views were developed.

### **Dashboard 1 — HR Workforce Overview**

The First dashboard provides:

* Total Employees
* Active Employees
* Exited Employees
* Attrition Rate
* Retention Rate
* Average Salary
* Average Performance Score
* Employees by Department
* Employees by Employment Type
* Attrition by Department
* Monthly Hours vs Performance Rating
* Salary Distribution
* Department slicer
* Gender distribution

### **Dashboard KPI Snapshot**

```text
Total Employees       : 10,047
Active Employees      : 9,619
Exited Employees      : 428
Attrition Rate        : 4.26%
Retention Rate        : 95.74%
Average Salary        : 1,393,347.24
Performance Score     : 3.51 / 5
```

### **Dashboard 2 — Workforce & Employee Performance**

The Second dashboard focuses on:

* Average performance by department
* Department productivity
* Attrition reasons
* Attrition by years at company
* Key HR insights
* HR recommendations

### **Key dashboard observations**

* IT has the highest employee exit count.
* Better Opportunity is the leading recorded attrition reason.
* Work-Life Balance is another major attrition reason.
* Marketing has the highest average project completion.
* Performance Rating 4 has the highest employee count.
* Retention and performance indicators provide a consolidated view of workforce health.

The project includes **two interactive Power BI dashboard views.**

### HR Workforce Overview


![HR Workforce Overview](Dashboard%20Images/HR%20Workforce%20Analytics%20%26%20Employee%20Performance%20Dashboard.png)



### Employee Performance & Attrition Analysis


![Employee Performance & Attrition Analysis](Dashboard%20Images/Employee%20Performance%20%26%20Attrition%20Analysis.png)


## 8️. Key Insights

### **Workforce**

* The final analytical dataset contains **10,047 employees**.
* IT is the largest department with **2,684 employees**.
* The workforce has **9,619 active and 428 exited employees**.

### **Attrition**

* Overall attrition is **4.26%**, while retention is **95.74%**.
* IT has the highest number of employee exits.
* **Better Opportunity** is the leading recorded attrition reason.
* **Work-Life Balance** is another prominent recorded reason.

### **Employee Turnover Factors**

Exited employees show lower average:

* **Job satisfaction:** 2.52 vs 3.42
* **Employee engagement:** 2.68 vs 3.47
* **Work-life balance:** 2.92 vs 3.43

Exited employees also show higher average overtime:

* **17.55 hours vs 13.59 hours**

### **Performance**

* Overall performance score is **3.51 / 5**.
* Marketing and IT have the highest department-level average performance rating at approximately **3.52**.

### **Salary**

* Overall average salary is approximately **1.39 million**.
* IT has the highest average salary at approximately **1.56 million**.

### **Productivity**

* Marketing has the highest average project completion at **5.25 projects**.
* HR has the lowest average project completion at **5.07 projects**.

### **Statistical Evidence**

The t-test indicates statistically significant differences between active and exited employees for:

* Job Satisfaction
* Overtime Hours
* Employee Engagement
* Work-Life Balance

**Salary was not statistically significant at the 5% level.**

## 9️. HR Recommendations

Based on the analysis, the following actions are recommended:

### **1. Strengthen Retention Programs**

Prioritize retention initiatives for departments with higher employee exit counts, particularly larger workforce groups such as IT and Sales.

### **2. Address Career Growth**

Because **Better Opportunity** is the leading recorded attrition reason, strengthen:

* Career development programs
* Internal mobility
* Promotion pathways
* Skill development opportunities

### **3. Improve Work-Life Balance**

The analysis shows lower work-life balance among exited employees. HR can review:

* Workload allocation
* Flexible working arrangements
* Overtime expectations
* Employee well-being programs

### **4. Monitor Overtime**

Exited employees average more overtime hours than active employees. Departments should monitor excessive overtime and evaluate workload distribution.

### **5. Improve Employee Engagement**

Exited employees show lower average engagement. Regular employee feedback, recognition programs, manager check-ins, and engagement surveys can help identify issues earlier.

### **6. Focus on Job Satisfaction**

The significant difference in job satisfaction suggests that HR should monitor employee satisfaction and address workplace concerns before they contribute to turnover.

### **7. Use Department-Level Productivity Metrics**

Continue monitoring average project completion by department to identify productivity gaps and opportunities for process improvement.

### **8. Establish Continuous HR KPI Monitoring**

HR teams can use the Power BI dashboard to regularly monitor:

* Attrition Rate
* Retention Rate
* Workforce Size
* Performance
* Salary
* Productivity
* Department-level trends

## 10. Project Deliverables

| **Deliverable**           | **Description**                                                |
| ------------------------- | -------------------------------------------------------------- |
| **Raw Dataset**           | Original employee workforce dataset                            |
| **Cleaned Dataset**       | Analysis-ready employee dataset                                |
| **Jupyter Notebook**      | Python, EDA, KPI, statistical and SQL analysis                 |
| **SQLite Database**       | Structured employees table for SQL analysis                    |
| **Power BI Dashboard**    | Interactive HR analytics dashboards                            |
| **Dashboard Screenshots** | Visual documentation of dashboard outputs                      |
| **README**                | Project methodology, SQL queries, insights and recommendations |

## 11. Repository Structure

The repository is organized as follows:

```text
HR-Workforce-Analytics-Employee-Performance-Dashboard/
│
├── README.md
│
├── Dataset/
│   └── HR Workforce Analytics & Employee Performance Dashboard.csv
│
├── Jupyter_notebook_HR Workforce Analytics/
│   └── HR Workforce Analytics.ipynb
│
├── Power BI/
│   └── HR Workforce Analytics & Employee Performance Dashboard.pbix
│
└── Dashboard Images/
    ├── Employee Performance & Attrition Analysis.png
    └── HR Workforce Analytics & Employee Performance Dashboard.png

## 12. Conclusion

The ***HR Workforce Analytics & Employee Performance Dashboard*** provides an end-to-end analytical solution for understanding workforce behavior, employee performance, productivity, salary, and attrition.

The project combines ***Python, Pandas, SQL, SQLite, statistical analysis, and Power BI*** to transform raw employee data into actionable HR insights.

The analysis identifies important differences between active and exited employees, particularly in ***job satisfaction, employee engagement, work-life balance, and overtime hours.*** These findings can help HR teams design targeted retention initiatives, improve employee experience, monitor workforce productivity, and support evidence-based workforce planning.

## 👤 Author

### Sanika Gawand

***Skills Demonstrated:*** Python • Pandas • NumPy • SQL • SQLite • Statistics • Power BI • Data Analysis • Data Visualization • Git • GitHub
