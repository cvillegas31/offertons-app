# offertons-app
## Overview

This is a high-level overview of how you could implement a photo upload and management solution using AWS services.

### Architecture

Here's an overview of the architecture:

- A React app hosted on S3 that allows users to upload photos and view photo details.
- An API Gateway API that exposes three REST APIs: one for listing photos, one for uploading photos, and one for retrieving photo details.
- Three Lambda functions, one for each API, that handles the business logic for that specific API.
- An Amazon DynamoDB table that stores the metadata for each photo, using a Single-Table Design.
- An Amazon S3 bucket that stores the uploaded photos.
- An Amazon CloudFront distribution that serves the React app and the API Gateway API.
- An AWS Lambda function that resizes the uploaded photos to WebP format using the Sharp library.
- An AWS Lambda layer that contains the common code and dependencies used by the other Lambda functions.

### Interactions

Here's how the different components interact with each other:

1. When a user uploads a photo using the React app, the app generates a pre-signed URL for uploading the photo to S3.
2. The user uploads the photo to S3 using the pre-signed URL.
3. S3 triggers the Lambda function that resizes the uploaded photo to WebP format.
4. The resized photo is stored back in the S3 bucket.
5. The Lambda function that handles photo uploads is triggered, which saves the photo metadata to DynamoDB.
6. The React app lists the uploaded photos by calling the list photos REST API.
7. When a user clicks on a photo, the app retrieves the photo details by calling the photo details REST API.
8. The CloudFront distribution serves the React app and the API Gateway API, caching responses as needed to improve performance.

### Steps

To implement this architecture, you could follow these steps:

1. Create an S3 bucket to store the uploaded photos.
2. Create an IAM policy that allows S3 to trigger the Lambda function that resizes the uploaded photos.
3. Create a Lambda function that resizes the uploaded photos to WebP format using the Sharp library.
4. Create an IAM policy that allows the Lambda function to access the S3 bucket and save the resized photos.
5. Create a Lambda function layer that contains the common code and dependencies used by the other Lambda functions.
6. Create an IAM policy that allows the Lambda functions to access the DynamoDB table.
7. Create an Amazon DynamoDB table to store the photo metadata, using a Single-Table Design.
8. Create three Lambda functions, one for each REST API, that handles the business logic for that specific API.
9. Create an Amazon API Gateway API that exposes the three REST APIs.
10. Configure the API Gateway API to use the Lambda functions as the backend.
11. Create a React app that allows users to upload photos and view photo details.
12. Host the React app on S3.
13. Create an Amazon CloudFront distribution that serves the React app and the API Gateway API, caching responses as needed to improve performance.
14. Configure the React app to generate pre-signed URLs for uploading photos to S3.
15. Test the solution to ensure that everything is working as expected.

Overall, this architecture provides a scalable and highly available solution for handling photo uploads and metadata, while also providing a responsive and user-friendly interface for viewing and managing photos.
