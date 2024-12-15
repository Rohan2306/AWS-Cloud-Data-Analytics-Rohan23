# Project 1: Exploratory Data Analysis

## Project Description:
This project analyzes awarded contract data from the City of Vancouver (including the Library, Police Board, and Park Board). The goal is to uncover patterns in vendor bid success rates, focusing on how bid amounts affect the likelihood of winning contracts.

## Project Title:
**Exploratory Data Analysis on Vancouver Group Contracts Dataset**

## Objective:
Analyze the relationship between bid amounts and the success rate of awarded contracts for the Vancouver Group. The analysis focuses on identifying key factors influencing vendor success by examining bid amounts, vendor bids, and awarded outcomes.

## Dataset:
The dataset contains 646 entries of contract bids made by the contractors or vendors for the projects posted publicly by the City of Vancouver group with the following features:
- **Bid Number**: Unique identifier for each bid
- **Bid Type**: Type of bid (e.g., Request for Proposal)
- **Description**: Description of the contract
- **Award Date**: Date when the contract was awarded
- **Vendor Name**: Name of the vendor or contractor
- **Bid Amount**: Monetary value of the bid (may have missing values)
- **Awarded**: Status indicating if the bid was awarded (Yes/No)

## Methodology:

### 1. Data Ingestion:
- Uploaded raw data into the AWS S3 bucket (cov-raw-roh) dedicated to raw data.
- Organized data by folder structure based on ingestion year and quarter.
- Configured the S3 storage class as Standard for frequent access, with lifecycle rules to transition to Glacier Flexible Retrieval after 90 days.

### 2. Data Profiling:
- Used AWS Glue DataBrew to profile the dataset and assess data quality.
- Identified missing values and duplicate rows.
- Stored profiling results in dedicated subfolders in the S3 bucket (cov-trf-roh).

### 3. Data Cleaning:
- Standardized column names by replacing space with underscores.
- Filled the missing values with NULL values.
- Dropped unnecessary columns.
- Stored cleaned data in CSV format for users and Parquet format for system processing.
- Results of data cleaning are stored in a separate dedicated S3 bucket (cov-trf-roh).

### 4. Data Pipeline Design:
- Designed a pipeline using AWS Glue with nodes for filtering, aggregating, and merging datasets.
- Extracted Awarded contracts and Bid Amount for analysis.
- Aggregated data to get the count of awarded contracts and total bids for each bid number and vendor name.
- Calculated contract awarded rate.
- Results of the exploratory analysis are stored in a separate bucket (cov-cur-roh).

### 5. Data Analysis:
- The dataset was analyzed to identify the link between Bid Amount and contract award likelihood.
- Contracts with specified bid amounts were compared against those with missing bid amounts to identify success rate trends.

## Tools & Technologies:
- **AWS S3**: Data Storage
- **AWS Glue DataBrew**: Data Profiling and Data Cleaning
- **AWS Glue Studio**: ETL Pipeline

## Deliverables:
- AWS Glue Data Pipeline for processing, aggregating, and merging the dataset.
- Data Profiling Report generated by AWS Glue DataBrew, highlighting data quality issues.
- Cleaned Data Files stored in S3 buckets in both CSV and Parquet formats.
- Visualization of the correlation between the bid amount and contract award rate.

## Insights & Findings:
- There is a strong correlation between specifying a Bid Amount and a 95% success rate for contract awards.
- A negative correlation exists between missing Bid Amounts and lower contract success rates.
- Vendors who included Bid Amounts in their bids show a positive correlation with higher success rates.
- The high percentage of missing Bid Amounts negatively affects data quality and weakens potential correlations in analysis.

## Visualizations:
- Draw.io diagram for data analytic platform for the City of Vancouver - Contracts


# Project 1: Descriptive Data Analysis

## Project Description:
This project analyzes the contracts awarded by the City of Vancouver group. The goal is to calculate the success rate of vendor bids and understand how effectively bids are being awarded.

## Project Title:
**Analyzing the Success Rate of Vendor Bids for the City of Vancouver Contracts**

## Objective:
Analyze how effective the bids proposed by vendors are by calculating the success rate of contracts awarded by the City of Vancouver group.

## Dataset:
The dataset includes 646 records of contract bids submitted by contractors or vendors for projects publicly listed by the City of Vancouver. Following are the features of the dataset:
- **Bid Type**: Request for Proposal
- **Bid Number**: Unique identifier for each bid
- **Bid Description**: Description of the contract
- **Award Date**: Date the contract was awarded
- **Vendor Name**: Name of the vendor or contractor
- **Bid Amount**: Monetary value of the bid
- **Awarded**: Status of the bid (Yes/No)

## Descriptive Analysis Question:
How effective are the bids proposed by vendors for contracts posted by the City of Vancouver group?

## Methodology:

### 1. Data Ingestion:
- Uploaded raw data to AWS S3 (cov-raw-roh) and organized it by year and quarter.
- Set S3 storage to Standard with lifecycle rules to move data to Glacier after 90 days.

### 2. Data Profiling:
- Utilized AWS Glue DataBrew to analyze the dataset and evaluate its quality.
- Identified missing values and duplicate rows, then stored the profiling results in dedicated subfolders.

### 3. Data Cleaning:
- Standardized column name by replacing the spaces with underscores.
- Deleted extra and unnecessary columns and duplicate rows.
- Stored cleaned data in CSV format for users and Parquet format for system processing.

### 4. Data Pipeline Design:
- Filtered the dataset to include only awarded contracts.
- Aggregated the total number of bids and awarded contracts, then calculated the success rate.
- Stored the results in the S3 (cov-trf-roh) bucket in CSV and Parquet formats.

## Tools & Technologies:
- **AWS S3**: Data storage
- **AWS Glue DataBrew**: Data profiling and cleaning
- **AWS Glue**: Data transformation and aggregation

## Deliverables:
- Raw and cleaned data are stored in CSV and Parquet formats in S3 buckets for efficient management.
- An AWS Glue pipeline is used for data transformation, aggregation, and calculating the success rate of awarded contracts.
- The data is then filtered and aggregated to determine the success rate of the contracts awarded.

## Insights & Findings:
- The overall bid success rate for awarded contracts is 31.5%.
- Certain vendors consistently achieve higher success rates, suggesting advantages in proposal quality or pricing.

## Visualizations:
- Draw.io diagram for data analytic platform for the City of Vancouver – Contracts


# Project 1: Diagnostic Analysis

## Project Description:
Diagnostic Analysis of Vendor Bids and Contract Awards at the City of Vancouver.

## Project Title:
**Investigating Data Quality, Completeness, and Structure of City of Vancouver Contract Bids Dataset**

## Objective:
The primary goal is to identify anomalies, missing data, inconsistencies, or patterns in the dataset that could impact its usability for generating data visualization, reports, and predictive modeling. Insights from this analysis will help uncover any issues that need to be addressed and guide the necessary data cleaning and transformation steps. This ensures the dataset is properly prepared and optimized for subsequent tasks, enabling accurate and effective analysis.

## Dataset:
The dataset contains details on contracts issued by the City of Vancouver. Following are the features of the dataset:
- **Bid Type**: Request for Proposal
- **Bid Number**: Unique identifier for each bid
- **Bid Description**: Description of the contract
- **Award Date**: Date the contract was awarded
- **Vendor Name**: Name of the vendor or contractor
- **Bid Amount**: Monetary value of the bid
- **Awarded**: Status of the bid (Yes/No)

## Methodology:

### Data Ingestion:
- Uploaded the raw dataset to Amazon S3 (bucket: cov-raw-roh).
- Organized data by year and quarter for structured storage and easy access.

### Data Profiling

#### Profiling Job Setup:
- Connected the dataset to AWS Glue DataBrew for profiling and quality assessment.
- Included all key fields:
  - **String Columns**: Bid_Number, Bid_Type, Vendor_Name, Awarded
  - **Numeric Columns**: Bid_Amount, Award_Date

#### Profiling Insights:
- **Data Quality**: Most columns contained valid values, but some columns contained missing values and duplicate entries.
- **Missing Values**:
  - **Bid_Amount**: 69% missing values, significantly impacting analysis.
  - **Vendor_Name**: A few missing entries were identified.
- **Duplicate Values**:
  - **Vendor_Name**: Unique identifiers, but some duplicates identified.

#### Storage of Results:
- Stored profiling results in Amazon S3 bucket (cov-trf-roh).

### Validation:
- **Missing Values**:
  - **Bid Amount**: 69% of the values were missing.
  - **Vendor Name**: There were a few missing entries, which could affect the analysis.
  - **Award Status**: There were no missing values identified in the Awarded field, ensuring completeness in terms of contract outcomes.
- **Duplicates**:
  - Duplicate entries were found in the Vendor Name field.

### Action Plan:
- To handle missing values, replace missing values with NULL values to indicate the absence of data.
- Remove all duplicate rows with the same entries.

### Outcome:
The diagnostic analysis identified key issues related to missing data, duplicates, and anomalies in the dataset. Addressing these issues will improve the dataset’s quality and ensure it is ready for accurate reporting, visualization, and predictive modeling.

## Tools & Technologies:
- **AWS Glue DataBrew**: Automated profiling to assess dataset quality.
- **Amazon S3**: Centralized storage for raw data and profiling results.

## Deliverables:
1. **Data Profiling Report**: Comprehensive report with data quality metrics, column statistics, and schema validation.
2. **Data Quality Insights**: Analysis of missing values, anomalies, and duplicates.
3. **Profiling Results Storage**: S3 Folder: Data profiling results are stored in the cov-trf-roh bucket.

## Visualizations:
- Draw.io diagram for data analytic platform for the City of Vancouver - Contracts


# Project 1: Data Wrangling

## Project Title:
**Data Wrangling for contracts awarded by the City of Vancouver**

## Objective: 
The goal of this project is to clean and structure data on vendor bids and contract awards at the City of Vancouver, improving its accuracy and usability for analyzing contract success rates, vendor performance, and bid trends.

## Background:
The data on vendor bids for contracts is often inconsistent, incomplete, or contains duplicates, making it hard to derive actionable insights. Effective data wrangling will ensure accuracy and completeness, enabling better analysis and decision-making in the contract award process.

## Dataset:
The dataset contains details on contracts issued by the City of Vancouver. Following are the features of the dataset:
- **Bid Type**: Request for Proposal
- **Bid Number**: Unique identifier for each bid
- **Bid Description**: Description of the contract
- **Award Date**: Date the contract was awarded
- **Vendor Name**: Name of the vendor or contractor
- **Bid Amount**: Monetary value of the bid
- **Awarded**: Status of the bid (Yes/No)

## Methodology:

### Data Collection & Preparation:
- **Data Ingestion**: Uploaded the raw dataset to Amazon S3 (bucket: cov-raw-roh).
- **Data Profiling**: Assess datasets for issues like missing values, duplicates, and inconsistent formats while documenting data types, formats, and discrepancies between datasets.

### Data Cleaning:
- Address missing values in key fields such as Bid Amount and Vendor Name, using imputation or exclusion depending on the significance of the data.
- Remove duplicates in the Bid Number field to ensure each bid is unique.
- Normalize categorical variables like Awarded Status to ensure consistency in values (e.g., "Yes"/"No" or "1"/"0").

### Data Transformation:
- Convert data types where necessary, such as converting Bid Amount to numeric values.
- Derive new features, such as Contract Award Rate (percentage of successful bids), to aid in the analysis of contract success.
- Aggregate data where needed, such as summarizing bid success by vendor.

## Tools and Technologies:
- **Amazon S3**: Centralized storage for raw and transformed data, ensuring easy access.
- **AWS Glue DataBrew**: Automates data cleaning and preparation for analysis.
- **AWS Glue**: Manages the data wrangling pipeline, automating transformation and consolidation.

## Deliverables:
- A cleaned dataset in CSV or Parquet format, ready for analysis.
- A report detailing the data wrangling process.
- Visualizations showing key insights and data quality checks.

## Visualizations:
- Draw.io diagram for data analytic platform for the City of Vancouver - Contracts


# Project 1: Data Quality Control

## Project Description:
Ensuring the contacts dataset meets quality standards by implementing control measures and audits to validate data accuracy and integrity.

## Project Title:
**Data Quality control for contracts published by the City of Vancouver.**

## Objective:
The objective of this project is to ensure that the contract posted by the City of Vancouver dataset meets high standards of quality, security, and observability. This involves implementing rigorous checks for data accuracy, completeness, and integrity, applying data security measures to protect sensitive information, and establishing observability solutions for real-time monitoring. These steps aim to deliver a reliable, secure, and trackable dataset for effective contract award analysis and informed decision-making by the City of Vancouver.

## Description:
High-quality data is vital for accurate analysis and decision-making. The dataset requires thorough checks to ensure its integrity and prevent errors.

## Scope: 
The scope of the dataset is to ensure that the dataset is reliable and usable for analysis and decision-making.

## Dataset:
The dataset contains details on contracts issued by the City of Vancouver. Following are the features of the dataset:
- **Bid Type**: Request for Proposal
- **Bid Number**: Unique identifier for each bid
- **Bid Description**: Description of the contract
- **Award Date**: Date the contract was awarded
- **Vendor Name**: Name of the vendor or contractor
- **Bid Amount**: Monetary value of the bid
- **Awarded**: Status of the bid (Yes/No)

## Methodology:

### Data Enriching:
- **AWS Glue**:
  - Created a data pipeline named “cov-cont-QPC-roh” to process clean data from the transform S3 bucket.
  - Enriched the dataset by adding Bid Amount to analyze the relationship between bid amounts and contract success rates.
  - Generated a data catalog using AWS Glue Crawlers to convert datasets into tables for easy querying.

### Data Governance:
- **Completeness and Uniqueness Rules**:
  - Applied data quality rules in AWS Glue DataBrew:
    - **Completeness Rule**: Ensured the Bid Number field was 95% complete.
    - **Uniqueness Rule**: Ensured the Vendor Name field was 99% unique.
- **Conditional Routing**:
  - Separated the results into “Passed” and “Failed” datasets using a conditional router node.
  - Stored the results in designated S3 folders:
    - Passed Results: `s3://cov-trf-roh/Contracts/data-quality/Passed/`
    - Failed Results: `s3://cov-trf-roh/Contracts/data-quality/Failed/`

### Data Security:
- **AWS KMS (Key Management Service)**:
  - Encrypted S3 buckets using customer-managed encryption keys to protect sensitive data.
  - Enabled bucket versioning to maintain data integrity and recover previous versions if necessary.
- **Cross-Region Replication**:
  - Implemented cross-region replication with encryption to ensure data availability and disaster recovery.

### Data Observability:
- **Amazon CloudWatch**:
  - Created dashboards to monitor key metrics, including:
    - Bucket Sizes and the Number of Objects in S3 buckets (Raw, Transformed, and Curated).
    - Billing Gauges to track costs associated with storage and compute resources.

## Tools and Technologies:
- **AWS Glue**: ETL data pipeline creation and data cataloging.
- **AWS S3**: Data storage and security measures.
- **AWS KMS**: Data encryption.
- **Amazon CloudWatch**: Observability and monitoring.

## Deliverables:
- A quality-checked dataset stored in AWS S3, with passed and failed results for contract analysis.
- Data governance rules and audit reports detailing the completeness and uniqueness checks.
- A secure data pipeline that ensures data integrity and privacy.
- Real-time observability and monitoring dashboards.

## Visualizations:
- Draw.io diagram for data analytic platform for the City of Vancouver - Contracts

# Project 2: Exploratory Data Analysis

## Project Description
This project involves exploratory analysis of the University Canada West program review datasets, which include student performance data and clickstream data showing the number of page visits. The goal is to explore the relationship between students' online study portal interactions (page visits) and their program performance, aiming to uncover meaningful patterns and insights.

## Project Title
Exploratory Data Analysis of University Canada West Students' Performance Data to Uncover Patterns and Insights

## Objective
Analyze the relationship between the number of page visits on the online study portal and student performance rates at University Canada West.

## Dataset
The dataset consists of two main components: **Student Performance List** and **Student ClickStream Data**, each containing 50 rows.

### Student Performance List

#### Features:
- **Student_ID**: Unique identifier for each student.
- **First_Name**: Student's first name.
- **Last_Name**: Student's last name.
- **Age**: Student's age.
- **Gender**: Student's gender (Male/Female).
- **Course_GPA**: GPA of the student in the course.
- **Attendance_Percentage**: Attendance percentage for the course.
- **Project_Score**: Score achieved in the course project.
- **Final_Exam_Score**: Score achieved in the final exam.
- **Program_Status**: Status of the student in the program (Pass/Fail).

_Update Frequency_: Quarterly.

### Student ClickStream Dataset

#### Features:
- **Student_ID**: Unique identifier for each student.
- **Page_Visited**: Name or URL of the page visited by the student.
- **Timestamp**: Date and time when the action occurred.
- **Action**: Type of action performed (e.g., Click, Scroll, Download).
- **Duration**: Time spent on the page (in seconds).

_Update Frequency_: Real-time or session-based aggregation.

## Purpose
Analyze student engagement and interaction patterns within the university’s digital platforms.

## Methodology

### 1. Data Ingestion:
- Uploaded raw data to the AWS S3 bucket (`ac-raw-roh`) dedicated to storing raw data.
- Organized the data into folders by year and quarter.
- Set the S3 storage class to Standard for frequent access, with lifecycle rules to move data to Glacier Flexible Retrieval after 90 days.

### 2. Data Profiling:
- Used AWS Glue DataBrew to analyze the dataset and check its quality.
- No missing or duplicate values were found.
- Stored profiling results in the S3 bucket (`ac-trf-roh`).

### 3. Data Cleaning:
- Standardized column names by replacing spaces with underscores.
- Removed unnecessary columns.
- Categorically mapped binary columns such as Program Status.
- Saved cleaned data in CSV format for users and Parquet format for system processing.
- Stored the cleaned data in the S3 bucket (`ac-trf-roh`).

### 4. Data Pipeline Design:
- Created a pipeline in AWS Glue for filtering, aggregating, and merging datasets.
- Extracted data on the Student Performance List and Student ClickStream for analysis.
- Aggregated the number of page visits and total number of students.
- Calculated the student performance rate.
- Stored the results in the S3 bucket (`ac-cur-roh`).

### 5. Data Analysis:
- The dataset was analyzed to identify the link between the number of page visits and students' performance (i.e., program status).

## Tools & Technologies
- AWS S3: Data Storage
- AWS Glue DataBrew: Data Profiling and Data Cleaning
- AWS Glue Studio: ETL Pipeline

## Deliverables:
- An AWS Glue Data Pipeline for processing, aggregating, and merging the dataset.
- A Data Profiling Report from AWS Glue DataBrew, stating no quality issues were found.
- Cleaned data files stored in S3 buckets in both CSV and Parquet formats.

## Insights & Findings:
- There is a strong correlation between student performance rate and the number of page visits.
- Students with more page visits had a better performance rate.

## Visualizations:
Draw.io diagram

---

# Project 2: Descriptive Data Analysis

## Project Description
This project develops a data analytics platform for the University Canada West to evaluate program performance using student, faculty, and department chair data. The platform enables data-driven insights through efficient data ingestion, cleaning, transformation, and comprehensive analysis to support evidence-based program reviews and continuous improvement.

## Project Title
Data Analytics Platform for Program Reviews at University Canada West

## Objective
Develop a comprehensive data analytics platform to support program review processes, encompassing descriptive analyses. This platform will evaluate program performance based on student, faculty, and department chair data to derive actionable insights.

## Dataset
The dataset consists of three components: **Student Performance List**, **Faculty Performance List**, and **Department Chair List**, each containing 50 rows.

### Student Performance List
Features are the same as described in the **Exploratory Data Analysis** section.

_Update Frequency_: Quarterly.

### Faculty Performance List

#### Features:
- **Faculty_ID**: Unique identifier for each faculty member.
- **First_Name**: Faculty member's first name.
- **Last_Name**: Faculty member's last name.
- **Age**: Faculty member's age.
- **Gender**: Faculty member's gender (Male/Female).
- **Courses_Taught**: List of courses taught by the faculty member.
- **Teaching_Experience_Years**: Number of years of teaching experience.
- **Student_Evaluation_Score**: Average score given by students in evaluations.
- **Research_Publications**: Number of research publications by the faculty member.
- **Performance_Rating**: Overall performance rating of the faculty member.

_Update Frequency_: Quarterly.

### Department Chair List

#### Features:
- **Department**: Name of the department offering the course.
- **Course_Code**: Unique identifier for the course.
- **Instructor**: Name of the instructor teaching the course.
- **Credits**: Number of credits for the course.
- **Enrollment**: Number of students enrolled in the course.
- **Course_Rating**: Average rating of the course.
- **Pass_Rate**: Percentage of students who passed the course.
- **Year_Offered**: Year when the course was offered.
- **Student_Feedback**: Aggregated feedback from students.
- **Chair_Comments**: Comments and observations by the department chair.

_Update Frequency_: Annually.

## Methodology

### 1. Data Ingestion:
- Uploaded raw datasets (student, faculty, department chair) to AWS S3 (`cov-raw-roh`) and organized it by year and quarter.
- Set S3 storage to Standard with lifecycle rules to move data to Glacier after 90 days.

### 2. Data Profiling:
- Utilized AWS Glue DataBrew to analyze the dataset and evaluate its quality.
- No duplicate or missing values were identified.

### 3. Data Cleaning:
- Standardized column names by replacing spaces with underscores.
- Deleted extra and unnecessary columns.
- Stored cleaned data in CSV format for users and Parquet format for system processing.

### 4. Data Pipeline Design:
- Filtered the dataset as per student program status.
- Aggregated the total number of students, faculty, and department chairs, then calculated the success rate of student performance, faculty performance, and department chair comments.
- Stored the results in the transform S3 (`ac-trf-roh`) bucket in CSV and Parquet formats.

## Tools & Technologies:
- AWS S3: Data Storage
- AWS Glue DataBrew: Data Profiling and Cleaning
- AWS Glue: Data Transformation and Aggregation

## Deliverables:
- Raw and cleaned data are stored in CSV and Parquet formats in S3 buckets for optimized management.
- An AWS Glue pipeline is utilized for data transformation, aggregation, and calculating the success rate of awarded contracts.
- The data is filtered and aggregated to assess the success rate of student performance, faculty performance, and department chair reviews.

## Insights & Findings:
- The student performance rate is 90%.
- The faculty performance rate is 95%.
- The department chair review success rate is 95%.

## Visualizations:
- Draw.io diagram

---

# Project 2: Data Quality Control

## Project Description
Implementing control measures and audits to ensure the student performance dataset meets quality standards and maintains data accuracy and integrity.

## Project Title
Data Quality Control for Student Performance Dataset for University Canada West

## Objective
The goal of this project is to ensure the Student Performance List dataset adheres to high standards of quality, security, and visibility. This includes implementing thorough checks for data accuracy, completeness, and integrity, applying robust security measures to safeguard sensitive student information, and setting up real-time monitoring solutions for continuous tracking. These efforts aim to provide a reliable, secure, and transparent dataset to support effective program performance analysis and data-driven decision-making at University Canada West.

## Dataset
The student performance dataset consists of 50 rows, featuring:
- **Student_ID**
- **First_Name**
- **Last_Name**
- **Age**
- **Gender**
- **Course_GPA**
- **Attendance_Percentage**
- **Project_Score**
- **Final_Exam_Score**
- **Program_Status**

## Tools and Technologies:
- **Amazon S3**: For centralized storage of raw, transformed, and curated datasets.
- **AWS Glue**: For data pipeline creation, data cataloging, and data quality checks.
- **AWS Glue DataBrew**: For profiling data quality, applying rules, and routing conditional outputs.
- **AWS KMS**: For encryption and secure data management.
- **Amazon CloudWatch**: For real-time monitoring, dashboards, and alerts.

## Methodology

### Data Enrichment:
- **AWS Glue**: Developed a data pipeline named “ac-pr-QPC-roh” to process clean data from the transformed S3 bucket. Enhanced the dataset by integrating the Clickstream Dataset, adding the number of page visits feature.

### Data Governance:
- **Completeness and Uniqueness Rules**: Applied data quality rules in AWS Glue DataBrew:
  - **Completeness Rule**: Ensured the Course_GPA field was 95% complete.
  - **Uniqueness Rule**: Ensured the Student_ID field was 99% unique.

### Conditional Routing:
- Divided the results into "Pass" and "Fail" datasets using a conditional router node.
- Stored the results in dedicated S3 folders:
  - **Passed Results**: s3://ac-trf-roh/Contracts/data-quality/Pass/
  - **Failed Results**: s3://ac-trf-roh/Contracts/data-quality/Fail/

### Data Security:
- **AWS KMS (Key Management Service)**: Encrypted S3 buckets using customer-managed encryption keys.
- **Cross-Region Replication**: Implemented to enhance data availability and disaster recovery.

### Data Observability:
- **Amazon CloudWatch**: Created dashboards to track key metrics such as bucket sizes, object counts, billing gauges, and Glue job logs.

## Deliverables:
- **Cleaned and Enriched Dataset**: A standardized dataset stored in Amazon S3 in both CSV and Parquet formats.
- **Data Quality Reports**: Reports outlining data that passed or failed completeness and uniqueness checks.
- **Secure Data Storage**: Encrypted S3 buckets with version control and cross-region replication.
- **CloudWatch Dashboards**: Real-time dashboards to monitor data quality, storage usage, and pipeline performance.

## Visualizations:
Draw.io diagram 

