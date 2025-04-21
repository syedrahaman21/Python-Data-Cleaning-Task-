Data Cleaning with Pandas

This project demonstrates how to clean a raw dataset using Python and Pandas. It includes step-by-step cleaning operations commonly used in data analysis.

Steps Performed:

1. Loaded dataset using pandas.read_csv()


2. Checked and handled missing values using .isnull(), .dropna(), and .fillna()


3. Removed duplicate rows with .drop_duplicates()


4. Standardized text data (e.g., customer_names, country_names) using .str.lower() and .replace()


5. Converted date columns like order_date and ship_date using pd.to_datetime()


6. Cleaned column names to lowercase and replaced spaces with underscores


7. Verified and corrected data types (e.g., int, float, datetime)


8. Dropped unnecessary columns using df.drop()



Tools Used:

Python

Pandas

Jupyter Notebook
