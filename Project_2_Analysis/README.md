# Project 2 Analysis

## Introduction

This project explores the data science job market with the goal of understanding how skills influence salaries and which roles offer the best opportunities.

The analysis focuses on identifying high-value skills, salary differences across regions, and the relationship between skill sets and compensation.

### Questions to Analyze

1. Do more skills lead to higher salaries?
2. How do salaries vary across regions?
3. What are the most in-demand skills?
4. What is the salary associated with the top skills?

### Excel Skills Used

- Pivot Tables  
- Pivot Charts  
- DAX (Data Analysis Expressions)  
- Power Query  
- Power Pivot  

### Dataset

The dataset contains information on job titles, salaries, locations and required skills. It is used to analyze trends and better understand how the data job market behaves.

---

## 1. Do more skills lead to higher salaries?

### Power Query (ETL)

#### Extract

Data was extracted using Power Query, creating two main queries:
- A dataset with job-related information  
- A dataset linking job IDs with skills  

#### Transform

Both datasets were cleaned and prepared by:
- Adjusting column types  
- Removing unnecessary fields  
- Cleaning text values

    - data_jobs_all

      ![Applied Steps](/Assets/Photos/applied_steps_1.png)

    - data_job_skills

      ![Applied Steps 2](/Assets/Photos/applied_steps_2.png)

#### Load

- Finally, I loaded both transformed queries into the workbook, setting the foundation for the subsequent analysis.
    - data_jobs_all

        ![Data Jobs All](/Assets/Photos/query_salary.png)

    - data_job_skills

        ![Data Job Skills](/Assets/Photos/query_skills.png)

### Analysis

#### Insights

- There is a positive correlation between the number of skills requested in job postings and the median salary, particularly in roles such as Senior Data Engineer and Data Scientist.
- Roles that require fewer skills, such as Business Analyst, tend to offer lower salaries, suggesting that more specialized skill sets command higher market value.

![Skills vs Salary](/Assets/Photos/skills_vs_salary_graph.png)

#### So What

- This trend highlights the importance of developing a broader and more specialized skill set for individuals aiming to access higher-paying roles.

---

## 2. What is the salary for data jobs across different regions?

### Skills: PivotTables and DAX

#### Pivot Table

- A PivotTable was created using the data model built with Power Pivot.
- The `job_title_short` field was placed in rows and `salary_year_avg` in values.
- A measure was added to calculate the median salary for United States roles:
     ``` =CALCULATE(
MEDIAN(data_jobs_all[salary_year_avg]),
data_jobs_all[job_country] = "United States"
) ```

#### DAX

- To calculate the median yearly salary:

  ```Median Salary := MEDIAN(data_jobs_all[salary_year_avg]) ```

### Analysis

#### Insights

- Roles such as Senior Data Engineer and Data Scientist show higher median salaries both in the US and globally, reflecting strong demand for advanced data skills.
- There is a clear salary gap between US and non-US roles, likely influenced by the concentration of technology companies in the US.

![Salary Comparison](/Assets/Photos/salary_analysis_graph.png)

#### So What

- These insights are useful for career planning and salary negotiations, helping professionals understand how location impacts compensation.

---

## 3. What are the top skills in data roles?

### Skill: Power Pivot

#### Power Pivot

- A data model was created by connecting `data_jobs_all` and `data_jobs_skills`.
- After cleaning the data in Power Query, relationships were established between both tables.

#### Data Model

- The relationship was created using the `job_id` column.

![Data Model](/Assets/Photos/Data_model.png)

#### Power Pivot Interface

- Power Pivot was used to refine the model and create measures efficiently.

![Power Pivot](/Assets/Photos/power_pivot_image.png)

### Analysis

#### Insights

- SQL and Python stand out as the most demanded skills, highlighting their importance in data-related roles.
- Cloud technologies such as AWS and Azure also appear frequently, reflecting the industry's shift toward cloud-based solutions.

![Skill Demand](/Assets/Photos/skill_job_analysis_graph.png)

#### So What

- Understanding which skills are most valued helps guide learning priorities and career development in the data field.

---

## 4. What is the pay associated with top skills?

### Skill: Advanced Charts (Pivot Chart)

#### Pivot Chart

- A combined PivotChart was created to display median salary and skill likelihood:
    - Primary axis: Median salary (column chart)
    - Secondary axis: Skill likelihood (line chart)

### Analysis

#### Insights

- Higher salaries are associated with skills such as Python, Oracle, and SQL, reinforcing their importance in high-paying roles.
- Skills such as PowerPoint and Word are linked to lower salaries, reflecting lower specialization.

![Top Skills Salary](/Assets/Photos/skill_salary_analysis_graph.png)

### So What

- Focusing on high-value technical skills significantly increases earning potential in the data industry.

---

## Conclusion

This project was developed to explore salary trends and skill demand within the data job market using Excel. By combining tools such as Power Query, PivotTables, DAX, and data visualization, it provides a structured view of how skills, location, and job roles influence compensation.

As a Business and Technology student with a strong interest in data and analytics, this project reflects my motivation to better understand the market and build relevant skills aligned with industry demand. It also represents a practical step toward developing analytical thinking and data-driven decision making.
