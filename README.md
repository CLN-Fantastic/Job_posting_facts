# Job_posting_facts Dashboard (2022-2023)

**PROJECT OVERVIEW**

*Objective:*
 This project provides a comprehensive look at global job posting trends, focusing on salary distributions across roles and companies, as well as geographic demand.


**SCOPE**

**The analysis covers**:

   - **Skill Requirements:** Categorizing 252 distinct skills across 10 different skill types required in the current market.

   - **Market Demand:** Identified Data Analyst (197K) as the most frequently posted role, followed closely by Data Engineer and Data Scientist.

   - **Salary Leaders:** Highlighted that Senior Data Scientists command the highest average salary at $154K.

   - **Platform Dominance:** Visualized that LinkedIn is the primary source of job postings, accounting for 190K entries.

   - **Top Paying Companies:** Comparing average salary offerings across top-tier companies like MSP Staffing  LTD, Mantys and ReServe.



    
    

        

**METHODOLOGY**
   **Data Cleaning:** Used MySQL to handle null values, standardize job titles, and format currency.

   **Data Modeling:** Established relationships between job roles, locations, and salary data.

   **Data Visualization:** Created an interactive dashboard in Power BI to enable year-over-year comparisons (2022 vs. 2023).

**TOOLS**
**MySQL:** Data cleaning and transformation.

**Power BI:** Data visualization and dashboard design.







```
**USE SQL CODES**

 __SQL__

-- 1. TOTAL DISTINCT SKILLS TYPE
SELECT COUNT(DISTINCT type) AS "Distinct Skills Type" 
FROM skills_dim;

-- 2. TOTAL DISTINCT SKILLS
SELECT COUNT(DISTINCT skills) AS "Distinct Skills" 
FROM skills_dim;


-- 3. DISTINCT JOB COUNTRIES
SELECT COUNT(DISTINCT job_country) AS "job_countries" 
FROM job_postings_fact;



-- 4. HIGHEST JOB POSTINGS BY JOB TITLE

SELECT JOB_TITLE_SHORT,COUNT(JOB_ID)
FROM job_postings_fact
GROUP BY JOB_TITLE_SHORT 
ORDER BY COUNT(JOB_ID) DESC;


-- 5. COUNTRIES WITH THE HIGHEST JOB POSTINGS
SELECT job_country,COUNT(job_id)
FROM job_postings_fact
GROUP BY job_country 
ORDER BY COUNT(job_id) DESC;


-- 6. TOP 5 JOB ROLES BY HIGHEST AVG YEARLY SALARY
SELECT 
    job_title_short,
    ROUND(AVG(salary_year_avg), 2) AS avg_salary
FROM job_postings_fact
WHERE salary_year_avg IS NOT NULL
GROUP BY job_title_short
ORDER BY ROUND(AVG(salary_year_avg), 2) DESC
LIMIT 5;


-- 7. COMPANIES WITH HIGHEST ANNUAL AVG SALARY
SELECT 
    c.name,
    AVG(j.salary_year_avg) AS avg_company_salary
FROM company_dim c
JOIN job_postings_fact j ON c.company_id = j.company_id
WHERE j.salary_year_avg IS NOT NULL
GROUP BY c.name
ORDER BY avg_company_salary DESC
LIMIT 5;


-- 8. RECRUITMENT CHANNEL DISTRIBUTION
SELECT 
    job_via, 
    COUNT(job_id) AS posting_count
FROM job_postings_fact
GROUP BY job_via
ORDER BY posting_count DESC;



