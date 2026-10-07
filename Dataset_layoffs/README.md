# Dataset_layoffs

This folder contains the raw data used by the project. The main file is `layoffs.csv`, which provides layoffs records for companies around the world.

## Contents

- `layoffs.csv` — raw layoffs records used as the input data for cleaning and analysis.

## What the dataset contains

Each row represents a company-related layoffs record and includes:

- Company name and location
- Industry classification
- Total number of employees laid off
- Percentage of employees laid off
- Date of the layoffs
- Funding stage
- Country
- Funds raised by the company, in millions

The dataset contains null values, blank values, inconsistent industry labels, trailing punctuation in country names, and date values that may need normalization.

## Recommended usage

Import `layoffs.csv` into MySQL or another supported database. The cleaning scripts expect a table named `layoffs` with columns matching the CSV headers.

```sql
LOAD DATA LOCAL INFILE 'Dataset_layoffs/layoffs.csv'
INTO TABLE layoffs
FIELDS TERMINATED BY ','
IGNORE 1 LINES;
```

The actual import command may require a JDBC or database-client-specific path and connection configuration. After loading the data, continue with the cleaning workflow in the [Data_cleaning folder](../Data_cleaning/README.md).

## Important notes

- The CSV is the source of truth for the initial project data.
- Values in the CSV may be incomplete or inconsistent and should not be assumed to be fully cleaned.
- Inspect the source before changing schema or data definitions, especially when adding new analysis fields.
