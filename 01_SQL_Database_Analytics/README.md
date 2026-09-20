# Module 1: Advanced SQL & Relational Database Analytics

## Project Overview
This project demonstrates advanced relational database querying and customer analytical techniques using SQL within a Python environment. The goal is to evaluate customer purchasing habits, calculate revenue metrics, and generate regional performance rankings.

## Key Skills & Concepts
- **Core Queries:** Multi-table `INNER JOIN`s, aggregate functions (`SUM`, `AVG`, `COUNT`), `GROUP BY`, and `ORDER BY`.
- **Advanced SQL:** Common Table Expressions (CTEs) for query modularity.
- **Window Functions:** `DENSE_RANK() OVER (PARTITION BY ...)` for regional ranking.
- **Environment:** In-memory SQLite execution via Python (`sqlite3` and `pandas`).

## Key Findings
- **High-Value Customers:** Identified top revenue-generating customers across global regions.
- **Regional Performance:** Ranked customers by total spend within their respective geographic zones to target retention programs.

## Files in Folder
- `sql_queries_and_analysis.ipynb`: Executable Jupyter Notebook containing schema design, sample data insertion, and advanced analytical queries.
