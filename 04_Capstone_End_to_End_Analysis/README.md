# Module 04: Global Developer Ecosystem & Compensation Analytics (Capstone)

An end-to-end data analytics project evaluating software developer compensation, labor allocation, remote work wage differentials, and global skill valuation.

---

## Pipeline Architecture
1. **Data Wrangling & Imputation:** Handled missing/invalid values via domain-specific conditional median imputation (`Pandas`).
2. **Relational Analytics:** Executed CTEs and Window Functions (`RANK()`, `AVG() OVER()`) in an in-memory `SQLite` database.
3. **Hypothesis Testing:** Evaluated remote vs. on-site salary parity using Welch's two-sample $t$-test (`SciPy`).
4. **Data Visualization:** Generated a publication-ready 4-panel analytics dashboard (`Seaborn`/`Matplotlib`).

---

## 📊 Relational SQL Analysis Query

```sql
WITH LanguageStats AS (
    SELECT 
        primary_language,
        COUNT(developer_id) AS total_developers,
        AVG(annual_compensation_usd) AS avg_salary,
        AVG(years_experience) AS avg_exp
    FROM developers
    GROUP BY primary_language
),
RankedStats AS (
    SELECT 
        primary_language,
        total_developers,
        ROUND(avg_salary, 2) AS avg_salary_usd,
        ROUND(avg_exp, 1) AS avg_experience_years,
        RANK() OVER (ORDER BY avg_salary DESC) AS salary_rank,
        ROUND(avg_salary - AVG(avg_salary) OVER(), 2) AS diff_from_market_avg
    FROM LanguageStats
)
SELECT * 
FROM RankedStats
ORDER BY salary_rank ASC;

```
How to Run
Navigate to this directory and execute the analysis script:

```Bash
cd 04_Capstone_End_to_End_Analysis
python capstone_end_to_end_analysis.py
