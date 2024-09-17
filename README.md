# Athletic Sales Analysis

## Background

This project analyzes sales data to gain insights into the sales of athletic wear across various cities in the U.S. over the years 2020 and 2021. The analysis focuses on identifying the cities with the highest sales figures, the top-performing retailers, and the periods with peak sales in women's athletic footwear.

## Requirements

This analysis comprises several steps to combine, clean, and analyze the sales data.

### 1. Combine and Clean the Data

- **Import Libraries and Dependencies:**
   ```python
   import pandas as pd
   import os
   ```

- **Read the CSV files into DataFrames:**
   ```python
   df_2020 = pd.read_csv('path_to_directory/athletic_sales_2020.csv')
   df_2021 = pd.read_csv('path_to_directory/athletic_sales_2021.csv')
   ```

- **Check Data Types and Null Values:**
   After loading the data, ensure that columns in both DataFrames match in name and data type. Combine the DataFrames using:
   ```python
   combined_df = pd.concat([df_2020, df_2021], ignore_index=True)
   ```

- **Convert `invoice_date` to a Datetime Type:**
   ```python
   combined_df['invoice_date'] = pd.to_datetime(combined_df['invoice_date'])
   ```

### 2. Determine which Region Sold the Most Products

- Utilize either `groupby` or `pivot_table` to summarize the data by region, state, and city, renaming the aggregated column to represent the total number of products sold.

### 3. Determine which Region had the Most Sales

- Again, use `groupby` or `pivot_table`, this time focusing on total sales.

### 4. Determine which Retailer had the Most Sales

- Summarize the data by retailer while capturing sales totals.

### 5. Determine which Retailer Sold the Most Women's Athletic Footwear

- Filter the combined DataFrame to focus on women's athletic footwear sales before summarizing.

### 6. Determine the Day with the Most Women's Athletic Footwear Sales

- Create a pivot table with `invoice_date` as the index and `total_sales` as values, then resample to find daily sales.

### 7. Determine the Week with the Most Women's Athletic Footwear Sales

- Resample the previously created pivot table to find weekly sales totals.

For example, that might look like:
```python
weekly_sales_resampled = daily_sales_resampled.resample('W').sum()
top_weekly_sales = weekly_sales_resampled.sort_values(by='Total Sales', ascending=False)
```

## Sources

- **Pandas Library**: [Pandas Documentation](https://pandas.pydata.org/docs/)
- **OS Library**: [OS Module Documentation](https://docs.python.org/3/library/os.html)



