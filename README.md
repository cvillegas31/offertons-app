# offertons-app
Overview
This is a high-level overview of how you could implement a photo upload and management solution using AWS services.

Here's an overview of the architecture:

A React app hosted on S3 that allows users to upload photos and view photo details.
An API Gateway API that exposes three REST APIs: one for listing photos, one for uploading photos, and one for retrieving photo details.
Three Lambda functions, one for each API, that handles the business logic for that specific API.
An Amazon DynamoDB table that stores the metadata for each photo, using a Single-Table Design.
An Amazon S3 bucket that stores the uploaded photos.
An Amazon CloudFront distribution that serves the React app and the API Gateway API.
An AWS Lambda function that resizes the uploaded photos to WebP format using the Sharp library.
An AWS Lambda layer that contains the common code and dependencies used by the other Lambda functions.
Here's how the different components interact with each other:

When a user uploads a photo using the React app, the app generates a pre-signed URL for uploading the photo to S3.
The user uploads the photo to S3 using the pre-signed URL.
S3 triggers the Lambda function that resizes the uploaded photo to WebP format.
The resized photo is stored back in the S3 bucket.
The Lambda function that handles photo uploads is triggered, which saves the photo metadata to DynamoDB.
The React app lists the uploaded photos by calling the list photos REST API.
When a user clicks on a photo, the app retrieves the photo details by calling the photo details REST API.
The CloudFront distribution serves the React app and the API Gateway API, caching responses as needed to improve performance.
To implement this architecture, you could follow these steps:

Create an S3 bucket to store the uploaded photos.
Create an IAM policy that allows S3 to trigger the Lambda function that resizes the uploaded photos.
Create a Lambda function that resizes the uploaded photos to WebP format using the Sharp library.
Create an IAM policy that allows the Lambda function to access the S3 bucket and save the resized photos.
Create a Lambda function layer that contains the common code and dependencies used by the other Lambda functions.
Create an IAM policy that allows the Lambda functions to access the DynamoDB table.
Create an Amazon DynamoDB table to store the photo metadata, using a Single-Table Design.
Create three Lambda functions, one for each REST API, that handles the business logic for that specific API.
Create an Amazon API Gateway API that exposes the three REST APIs.
Configure the API Gateway API to use the Lambda functions as the backend.
Create a React app that allows users to upload photos and view photo details.
Host the React app on S3.
Create an Amazon CloudFront distribution that serves the React app and the API Gateway API, caching responses as needed to improve performance.
Configure the React app to generate pre-signed URLs for uploading photos to S3.
Test the solution to ensure that everything is working as expected.
Overall, this architecture provides a scalable and highly available solution for handling photo uploads and metadata, while also providing a responsive and user-friendly interface for viewing and managing photos.
