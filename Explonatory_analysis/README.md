# Exploratory_analysis

This folder contains SQL queries used to explore the cleaned layoffs dataset. The queries summarize layoffs by company, industry, country, funding stage, date, and year, and provide examples of rolling totals, rankings, and country-specific analysis.

## Contents

- `Exploratory Analysis.sql` — SQL queries for descriptive and exploratory analysis of layoffs data.

## What this folder does

The analysis script includes queries for:

- Retrieving the complete cleaned dataset
- Finding maximum layoffs and maximum percentages
- Ranking companies by total layoffs
- Summarizing layoffs by industry and country
- Grouping layoffs by year and month
- Calculating rolling totals over time
- Analyzing layoffs by funding stage
- Calculating average percentages by company
- Finding the top companies and years for each company
- Identifying the five highest-ranked company-year combinations
- Filtering records for Pakistan

## Expected input

The queries expect a cleaned table named `layoffs_staging2` with the following relevant columns:

- `company`
- `industry`
- `total_laid_off`
- `percentage_laid_off`
- `date`
- `stage`
- `country`
- `funds_raised_millions`

Run the cleaning workflow first so the staging table contains normalized data. The cleaned table can then be queried by executing the statements in `Exploratory Analysis.sql`.

## Running the analysis

1. Complete the cleaning workflow.
2. Confirm that `layoffs_staging2` exists and contains the expected columns.
3. Open `Exploratory Analysis.sql` in a MySQL-compatible database client.
4. Execute individual queries or the full script, noting that some queries produce zero or no results for a particular filter.
5. Export or visualize the results as needed for a report or dashboard.

## Important notes

- Some queries use MySQL-specific functions, including `YEAR`, `SUBSTRING`, and `STR_TO_DATE`.
- The table name and query behavior depend on the final cleaned table produced by the cleaning script.
- The final results should be tested with representative data before being used for business or policy decisions.
- This folder provides query examples rather than a complete user interface or automated reporting system.
