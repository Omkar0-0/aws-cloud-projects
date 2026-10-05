# Project 02 — Event-Driven S3 → Lambda → CloudWatch Logs

## Overview

A hands-on AWS project demonstrating an event-driven workflow using Amazon S3, AWS Lambda, and Amazon CloudWatch Logs.

When a file is uploaded to an Amazon S3 bucket, the S3 event triggers a Lambda function. The Lambda function processes the event and records the S3 bucket and uploaded object details in CloudWatch Logs.

## Architecture

```text
User
  │
  │ Upload File
  ▼
Amazon S3
  │
  │ S3 Event
  ▼
AWS Lambda
  │
  │ Log Event Details
  ▼
Amazon CloudWatch Logs
```

## AWS Services Used

- Amazon S3
- AWS Lambda
- Amazon CloudWatch Logs
- AWS IAM

## Project Workflow

1. Created an Amazon S3 bucket.
2. Created an AWS Lambda function.
3. Configured an S3 object-upload event to trigger Lambda.
4. Uploaded a test file to the S3 bucket.
5. S3 generated an event and invoked the Lambda function.
6. Lambda processed the S3 event.
7. Bucket and object details were written to CloudWatch Logs.
8. Verified the complete S3 → Lambda → CloudWatch event flow.

## Lambda Function

The Lambda function receives the S3 event and extracts information about the uploaded object, including:

- S3 bucket name
- Object key

The extracted information is written to the Lambda execution logs in Amazon CloudWatch Logs.

## Testing

A test file was uploaded to the configured S3 bucket.

The upload was used to verify that:

```text
S3 Upload
    ↓
S3 Event
    ↓
Lambda Invocation
    ↓
CloudWatch Logs
```

The Lambda execution and S3 object details were verified through CloudWatch Logs.

## Key Learning Outcomes

- Understanding event-driven architecture
- Working with Amazon S3 event notifications
- Configuring S3 to trigger Lambda
- Processing S3 events using Lambda
- Working with CloudWatch Logs
- Verifying an end-to-end AWS event workflow
- Understanding IAM permissions required for AWS service integration

## Cleanup

After completing the testing, the AWS resources used for the project were cleaned up to avoid unnecessary AWS charges.

## Project Status

**Completed**
