# API Gateway Challenge

## Background
A cloud engineer working for Company X created a Cloudformation template to deploy a serverless API
service which will receive and store data about sports teams into a NoSQL database.

After deploying the stack, although the AWS Cloudformation stack is successfully created, when the API
receives a POST request the engineer is facing some issues and data is not being written to the table as
expected.

The Cloudformation stack mainly deploys the following AWS resources:

|Service        |Description|
|---------------|-----------|
|API Gateway    |Handles the http traffic|
|Role           |Role to be used by Lambda Function|
|Lambda Function|Extract data from the http request and update the database|
|DynamoDB Table |NoSQL Database|

## Tasks
Based on this scenario, please work on below tasks:

**Main Task  [COMPLETED]**
- Make the necessary changes so data is successfully written to the DynamoDB Table once a
POST request is received by the API Gateway.

**Secondary Task  [COMPLETED]**

Pick one of following:

- Add any required resources to send a message to a SNS Topic whenever a new item is added to
the DynamoDB Table.
    - The message can be either table updated or the content of the new item added.
## Work I have done
 **Main Task Solution**
 
 - Updated IAM Role Permission for Lambda, I removed the * for Lambda and Added PutItem for DynamoDB 
 - Created Environment Variable that makes DynamoDB table name reference in code. (With interinsic functions it was getting little messy) 
 
 **Secondary Task**
 - Created SNS Topic,  Lambda, and Enabled Stream in DynamoDB strea with NEW_AND_OLD_IMAGES specification 
 - IAM role for Notification Lambda consist the CloudWatch Logs as well for better unit testing 
 - Kept security for IAM to limit the only items in which is required 
 ## Deployment: 
 Deploy the cf_template.yml providing name. (Should not have any special character) 
 Subscribe to the SNS Topic listed in output section
 
 ## IMPROVEMENTS: 
- The Notification can be improved with more detailing with JSON Parsing
- Main Processor Lambda should be enabled with CloudWatch for more unit testing(Just IAM Update) 
- Resources have been created with default names, we should put some more logical names
- Stacks can be separated for IAMs, Lambdas, and API govern by Import-Export, to make it more moduler and easy for updates 

