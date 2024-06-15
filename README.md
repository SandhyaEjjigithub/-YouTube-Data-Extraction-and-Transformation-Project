# YouTube-Data-Extraction-and-Transformation-Project

# Step 1: Create a YouTube Data API
Go to the Google Developer Console.
Create a new project and enable the YouTube Data API.
Generate API credentials which will be used to access the YouTube Data API.
# Step 2: Access YouTube Data API
Visit the YouTube Data API website.
Download the sample code provided for various programming languages (preferably Python).
# Step 3: Obtain Channel ID
Navigate to the YouTube channel and open any video.
Right-click and select "View Page Source".
Press Ctrl + F and search for channelId to find the channel ID.
# Step 4: Extract Data Using the Channel ID
Using the channel ID, you can extract the following data sections:
Channel Data
Videos Data
Comments Data
The data will be retrieved in JSON format.

# Step 5: Data Extraction with AWS Lambda
Use AWS Lambda to run your Python code for data extraction.
Store the raw data in an AWS S3 bucket.
# Step 6: Data Transformation with AWS Glue and Apache Spark
Use AWS Glue for ETL (Extract, Transform, Load) processes.
Employ Apache Spark (PySpark) for data processing within Glue.
Save the transformed data back to AWS S3.
# Step 7: Data Storage in Snowflake
Store the transformed data in Snowflake, a cloud data warehousing tool.
# Step 8: Visualization with Power BI
Integrate Power BI to create interactive dashboards and analyze the data.
# Automation Overview
AWS CloudWatch triggers the Lambda function.
The Lambda function calls the Glue job for data transformation.
The transformed data is saved to S3.
Snowpipe automatically loads the data into Snowflake tables.

# Lambda Function Configuration
Go to Configurations → Permissions.
Attach permissions:
S3 full permission
AWS Glue service role


# Creating Pipeline Connection from AWS to Snowflake
Create a new IAM role in AWS with S3 full access.
Copy the STORAGE_AWS_ROLE_ARN from AWS IAM roles and use it during Snowflake storage integration.
Define the integration in Snowflake, noting the STORAGE_AWS_IAM_USER_ARN and STORAGE_AWS_EXTERNAL_ID.
Update the AWS role's trust relationship with these values.
Describe the Snowflake pipe (DESC PIPE PIPENAME) and use the notification channel to create an event notification in S3 bucket properties.


# Connecting Power BI to Snowflake
Open Power BI and select "Get Data".
Choose "Snowflake" as the data source.
Enter the Snowflake server URL and warehouse name:
Copy the URL from the Snowflake account info, remove http://, and paste it in the server field.
Enter the warehouse name you are working with.
