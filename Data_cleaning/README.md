# Data_cleaning

This folder contains the SQL workflow used to prepare the raw layoffs dataset for analysis. The script stages the source data, identifies duplicate records, normalizes common inconsistencies, and removes records that do not contain enough usable information.

## Contents

- `Data-Cleaning.sql` — MySQL SQL statements for cleaning and standardizing the layoffs data.

## What this folder does

The cleaning workflow currently performs the following tasks:

1. Reads data from the `layoffs` table.
2. Creates staging tables for intermediate results.
3. Detects duplicate rows based on selected company and record fields.
4. Removes duplicate records.
5. Trims whitespace from company names.
6. Standardizes industry labels, including common Crypto variants.
7. Removes trailing punctuation from country names.
8. Converts date values to the MySQL `DATE` type.
9. Handles missing or blank industry values by using available values from related records.
10. Removes rows that do not contain both total layoffs and percentage layoffs.
11. Drops the temporary row-number column before the final cleaned data is used.

## Expected input

The script expects a source table named `layoffs` containing the columns from the CSV file:

- `company`
- `location`
- `industry`
- `total_laid_off`
- `percentage_laid_off`
- `date`
- `stage`
- `country`
- `funds_raised_millions`

The source data should be imported from [Dataset_layoffs/layoffs.csv](../Dataset_layoffs/layoffs.csv) before executing the script.

## Running the workflow

1. Create and populate the `layoffs` table from the CSV source.
2. Open `Data-Cleaning.sql` in a MySQL-compatible client.
3. Execute the script in order.
4. Review the staging tables and the cleaned records before using them in other queries.

> The script creates intermediate staging tables rather than automatically producing a single finalized table name. The final table name and export process may need to be adjusted to match the intended database workflow.

## Important notes

- The file uses MySQL-specific syntax such as `STR_TO_DATE`, `TRIM`, and table-alteration statements.
- The script includes exploratory statements and several generated staging tables. Execute it carefully because it may create or modify database objects.
- Review the duplicate-key and missing-value rules before using the cleaned records for a production analysis.
- The cleaning process should be tested against a copy of the source data before changing the production dataset.
