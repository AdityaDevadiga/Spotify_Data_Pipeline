# Spotify Data Pipeline End-to-End Python Data Engineering Project
Overview
This project implements a complete data pipeline for extracting, transforming, and loading (ETL) Spotify data using Python. The pipeline includes AWS Lambda functions for data extraction, transformation, and deployment, along with an architecture involving S3, Glue, and Athena.

 # Architecture
The project follows a serverless architecture on AWS:
<img width="949" alt="SPOTIFY_Project Architecture Diagram" src="https://github.com/AdityaDevadiga/Spotify_Data_Pipeline/assets/72966036/66e2ea34-9807-4b13-ae5b-3db36e7771d2">


# AWS Lambda Functions:

Data Extraction Lambda (lambda_handler in spotify_data_extraction.py):

Extracts data from the Spotify API using the spotipy library.
Uploads the raw data in JSON format to an S3 bucket (raw_data/to_processed/).
Triggered automatically based on a schedule or event.
Data Transformation Lambda (lambda_handler in spotify_data_transformation.py):

Reads raw JSON data from the S3 bucket.
Transforms the data into structured DataFrames (albums, artists, songs) using Python and Pandas.
Cleans and processes the data.
Stores the transformed data as CSV files in the S3 bucket (transformed_data/).
Triggered automatically after the extraction.
 # AWS S3:

Used for storing both raw and transformed data.
Bucket: spotify-etl-project-adityadev.
 # AWS Glue:

Optionally used for ETL jobs.
Crawls the S3 bucket and creates a metadata catalog.
Transforms raw data into structured tables.
 # AWS Athena:

Optionally used for querying and analyzing data stored in S3.
Usage
Setting up Spotify API credentials:

Obtain your Spotify API client ID and client secret.
Set these as environment variables: client_id and client_secret.
Deploying the Data Extraction Lambda:

Create an AWS Lambda function using the code in spotify_data_extraction.py.
Configure environment variables and set up triggers (e.g., CloudWatch Events).
Deploying the Data Transformation Lambda:

Create another Lambda function using the code in spotify_data_transformation.py.
Set environment variables and configure triggers (e.g., S3 event trigger after the extraction).
Monitoring:

View Lambda logs in AWS CloudWatch for monitoring and debugging.
Additional Notes
Make sure to grant the necessary IAM roles and permissions to Lambda functions.
Customize the Lambda function code as needed for your specific use case.
Adapt the S3 bucket names and paths based on your project structure.
License
This project is licensed under the MIT License.
