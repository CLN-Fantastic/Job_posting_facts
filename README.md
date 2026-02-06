# Job_posting_facts Dashboard (2022-2023)

**PROJECT OVERVIEW**
   *Objective*
This projects provides a comprehensive look at global job posting trends, focusing on salary distributions across roles and companies, as well as geographic demand.


**SCOPE**
   -The analysis covers:
-The highest Job Postings(job_title)specific
-Different types of skills needed for postings
-Showcase of distinct job countries


**METHODOLOGY**
- Data cleaning using MySQL
-
-
-



**DATA SOURCE**
The data was collected from a website which was provided by  youtube tutor called Luke Barousse.

**TOOLS**
-MySQL: Data cleaning 
-Power BI: Data Visualization


---

## Key Insights & Captions

### 1. High-Value Roles
**Senior Data Scientists** and **Senior Data Engineers** lead the market in average annual salary, significantly outpacing Machine Learning and Software Engineering roles in this dataset.
* **Top Salary:** Senior Data Scientist (~260M units).

### 2. Geographic Hotspots
There is a massive surge in job postings originating from **Vietnam (2,423 postings)**, dwarfing other countries in this specific subset like Zambia and Zimbabwe. This suggests a booming tech outsourcing or regional growth hub.

### 3. Salary Distribution by Company
The pie chart illustrates a relatively balanced salary expenditure among top firms. **Capital One** and **Meta** appear to be among the top contributors to the total salary volume.

### 4. Skills Ecosystem
The data tracks **252 distinct skills** categorized into **10 main types**, showing a diverse requirement set for modern technical roles.



```
**USE SQL CODES**

 __SQL__

--QUERY TO SHOW TOTAL DISTINCT SKILLS TYPE

SELECT COUNT(DISTINCT TYPE) AS "DISTINCT SKILLS TYPE" from SKILLS_DIM;


--QUERY TO SHOW TOTAL DISTINCT SKILLS

SELECT COUNT(DISTINCT SKILLS_DIM) AS "DISTINCT SKILLS" from SKILLS_DIM;


--QUERY TO SHOW DISTINCT JOB_COUNTRIES

SELECT COUNT(DISTINCT JOB_COUNTRY) AS JOB_COUNTRIES FROM job_postings_fact;


--TOP 5 JOBS WITH THE HIGHEST AVG_YEAR_SALARY

SELECT DISTINCT JOB_TITLE_SHORT,SUM(salary_year_avg) FROM job_postings_fact
GROUP BY JOB_TITLE_SHORT ORDER BY SUM(salary_year_avg) DESC;


