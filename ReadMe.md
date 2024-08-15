# Lending Club Data Engineering Project

## Project Overview

Lending Club, a peer-to-peer lending platform, needs to enhance its decision-making capabilities for loan approvals by leveraging historical data. The goal is to develop a system that can clean, process, and analyze loan data to generate accurate loan scores. These scores will help in assessing the creditworthiness of loan applicants more effectively.

## Datasets Used

The primary dataset used in this project is from Lending Club, a peer-to-peer lending platform. It contains comprehensive loan data which is critical for evaluating and analyzing loan applications.

- **Dataset Size**: 1.7 GB
- **Format**: CSV
- **Columns**: 118
- **Records**: Over 2 million

You can access the dataset [here](https://www.kaggle.com/datasets/wordsforthewise/lending-club/).

## Data Source Mock Up

In a real-world scenario, fintech datasets are typically large and consist of multiple files. To simulate this complexity, the original single CSV file has been divided into the following separate datasets for the purpose of this project:

1. **Customers**: Contains information about the loan applicants, including personal and financial details.
2. **Loans**: Includes details about the loans issued, such as loan amounts, terms, and statuses.
3. **Loan Repayments**: Tracks repayment history, including amounts paid and dates.
4. **Loan Defaulters**: Records instances of loan defaults and delinquencies.

All these datasets are in CSV format and represent a simplified version of what would be encountered in a large-scale financial dataset.

## 1. Data Cleaning

* **Objective**: Clean raw data from various CSV files to prepare it for analysis.
* **Approach**:
  - **Changing to Suitable Datatype**: Ensured all columns have the appropriate datatype for efficient processing.
  - **Renaming Columns**: Updated column names to be more descriptive and consistent across datasets.
  - **Removing Null Values**: Identified and handled missing values to prevent data quality issues.
  - **Adding Ingestion Date**: Included a timestamp for when the data was ingested, for better traceability.
  - **Stored Cleaned Data to Data Lake**: Saved the cleaned datasets to a central data lake for easy access and further processing.

## 2. Data Processing

* **Objective**: Process the cleaned data to create a comprehensive view and perform analysis.
* **Approach**:
  - **Created External Tables**: Defined external tables for each type of data to facilitate access for other teams.
  - **Created a View for Overview**: Developed a view that provides a consolidated overview of the complete loan data.
  - **Weekly Overview Table**: Implemented a table for a single overview of complete loan data, updated weekly by a script to ensure quick access to the most recent data.
  - **Loan Score Calculation**: Computed loan scores based on:
    - Loan Repayment History: Assessed payment history for score determination.
    - Loan Defaulters History: Evaluated historical default data.
    - Customer's Financial Health: Analyzed financial health metrics of customers.

## 3. Loan Score Calculation

This phase calculates loan scores based on various criteria and assigns final grades to each loan.

* **Criteria for Scoring**:
  1. **Payment History**: Evaluates the payment history based on recent payments and total payments received.
  2. **Loan Defaults History**: Assesses the loan default history, including delinquencies, public records, and bankruptcies.
  3. **Financial Health**: Considers loan status, home ownership, credit limits, and loan grades.
* **Final Score Calculation**: Combines the scores from the above criteria with predefined weightings to calculate the final loan score and assign grades.

## 4. Final Outputs

* **Processed Data**: Stores the final loan scores and grades in Parquet format for further analysis or reporting.

## Files

1. **1_lendingclub_data_ingestion.ipynb**: Handles data ingestion from CSV files.
2. **2_lendingclub_data_cleaning.ipynb**: Performs initial data cleaning and transformation.
3. **3_lendingclub_data_schema.ipynb**: Defines and applies data schemas.
4. **4_lendingclub_data_transformations.ipynb**: Applies additional data transformations.
5. **5_lendingclub_data_quality_checks.ipynb**: Conducts data quality checks and validations.
6. **6_lendingclub_data_processing.ipynb**: Processes the cleaned data and prepares it for analysis.
7. **7_lendingclub_data_pipeline.ipynb**: Manages the data pipeline for continuous data integration.
8. **8_lending_club_final_cleaning.ipynb**: Final data cleaning and preparation for analysis.
9. **9_lendingclub_loan_score_calculator.ipynb**: Calculates loan scores based on various criteria.

## Dependencies

- Apache Spark
- PySpark
- Hadoop

## Setup

1. Clone the repository:
    ```bash
    git clone <repository-url>
    ```
2. Set up a Spark environment: Follow the instructions [here](https://spark.apache.org/docs/latest/) to set up Spark and Hadoop.
3. Configure Spark session with appropriate settings for your environment.
4. Run the notebooks in the order provided to ensure proper data processing and analysis.

