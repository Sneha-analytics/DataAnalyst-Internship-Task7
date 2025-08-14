# DataAnalyst-Internship-Task7
# Task 7: Get Basic Sales Summary from a Tiny SQLite Database using Python

## **Objective**
The objective of this task is to connect Python to a small SQLite database, run basic SQL queries to get a sales summary (like total quantity sold and total revenue), and display the results using print statements and a simple bar chart.

## **Tools**
- Python (with `sqlite3`, `pandas`, `matplotlib`)
- SQLite (built-in with Python)
- Jupyter Notebook or `.py` file

## **Dataset**
- `sales_data.db` — Contains one table: `sales`  
  **Columns:** `product`, `quantity`, `price`

## **Steps Performed**
1. Created a small SQLite database `sales_data.db` with a table `sales`.
2. Connected to the SQLite database using `sqlite3.connect()`.
3. Ran SQL queries to calculate:
   - Total quantity sold per product
   - Total revenue per product (`SUM(quantity * price)`)
4. Loaded the results into a Pandas DataFrame.
5. Printed the summary table.
6. Created a bar chart of revenue per product using Matplotlib.
7. Saved the chart as `sales_chart.png`.

## **Code Overview**
```python
import sqlite3
import pandas as pd
import matplotlib.pyplot as plt

# Connect to database
con = sqlite3.connect("sales_data.db")

# SQL query for sales summary
query = """
SELECT product,
       SUM(quantity) AS total_quantity,
       SUM(quantity * price) AS revenue
FROM sales
GROUP BY product
"""

# Load query results into DataFrame
df = pd.read_sql_query(query, con)

# Display results
print(df)

# Plot bar chart
df.plot(kind='bar', x='product', y='revenue', legend=False)
plt.title("Revenue by Product")
plt.savefig("sales_chart.png")
plt.show()

# Close connection
con.close() ```

## **Deliverables**
Python script / Jupyter Notebook

SQLite database (sales_data.db)

sales_chart.png file
