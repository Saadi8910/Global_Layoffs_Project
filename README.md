# Global Layoffs Project

This project performs data cleaning and exploratory analysis on a global layoffs dataset. It is designed to help users examine layoffs by company, industry, country, funding stage, date, and the number of people affected.

## Project purpose

The project contains a raw dataset, a MySQL-based cleaning workflow, and SQL queries for exploratory analysis. The cleaned results are intended to support questions such as:

- Which companies and industries reported the largest layoffs?
- How many layoffs occurred in different countries or years?
- Which funding stages are associated with layoffs?
- How much a company affected as a percentage of its workforce?
- How layoffs changed over time?

## Project structure

- [Dataset_layoffs](Dataset_layoffs/) contains the source CSV file.
- [Data_cleaning](Data_cleaning/) contains the SQL workflow used to clean and standardize the data.
- [Explonatory_analysis](Explonatory_analysis/) contains SQL queries that summarize and explore the cleaned data.

## Dataset fields

The source data contains the following columns:

| Column | Description |
|---|---|
| `company` | Company name |
| `location` | Location associated with the company |
| `industry` | Company industry |
| `total_laid_off` | Number of employees laid off |
| `percentage_laid_off` | Percentage of employees laid off |
| `date` | Date when the layoffs occurred |
| `stage` | Company funding stage |
| `country` | Country associated with the company |
| `funds_raised_millions` | Funds raised by the company, in millions |

## Workflow

1. Load or import `Dataset_layoffs/layoffs.csv` into a MySQL database as a table named `layoffs`.
2. Run `Data_cleaning/Data-Cleaning.sql` to create a staging table, remove duplicate records, standardize values, correct date formats, fill missing industry values where possible, and remove records that do not contain usable layoff information.
3. Review the cleaned data in the resulting staging table or export it to a new table.
4. Run the queries in `Exploratory_analysis/Explonatory Analysis.sql` against the cleaned data.

> The cleaning and analysis scripts are designed for MySQL. Review the SQL statements before running them in another database engine because some statements use MySQL-specific syntax.

## Getting started

### Prerequisites

- MySQL or a MySQL-compatible database
- A database client that can execute SQL files
- Access to the source CSV file in the repository

### Example

```sql
CREATE TABLE layoffs (
    company TEXT,
    location TEXT,
    industry TEXT,
    total_laid_off INT,
    percentage_laid_off DOUBLE,
    date TEXT,
    stage TEXT,
    country TEXT,
    funds_raised_millions INT
);
```

Import the CSV into the `layoffs` table, then execute the cleaning script. The scripts refer to the table name `layoffs` and the expected columns, so the import process must preserve those names.

## Important notes

- The cleaning script creates and populates staging tables; it does not automatically rename a final cleaned table.
- Some rows may contain missing or inconsistent values. The script aims to normalize common issues, but data-quality review may still be needed.
- The exploratory queries provide analysis examples rather than a single completed dashboard or report.
- The source data is from Kaggle and should be treated according to its licensing and usage terms.

## Contributions

When adding new cleans or analyses, keep each operation in its corresponding folder, document the expected input and output, and update this README if the project structure or workflow changes.
