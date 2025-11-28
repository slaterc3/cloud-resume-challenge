# Project Context: AWS Cloud Resume Challenge

We are building the AWS implementation of the "Cloud Resume Challenge." The goal is to deploy a personal resume website using a serverless architecture, fully automated via Infrastructure as Code (Terraform).

## Core Objective
Build a static website with a dynamic "visitor counter" feature, hosted on AWS, using purely programmatic deployment methods (avoiding "ClickOps" in the AWS Console).

## Architecture Stack
1.  **Frontend:**
    * Static HTML/CSS/JS resume.
    * Storage: **Amazon S3** (Static Website Hosting).
    * CDN/Security: **Amazon CloudFront** (HTTPS enforcement).
    * DNS: **Route 53** (Custom domain management).

2.  **Backend (Visitor Counter):**
    * Logic: **AWS Lambda** (Python) to retrieve/update visitor counts.
    * Database: **Amazon DynamoDB** (NoSQL) to store the atomic counter.
    * API: **Amazon API Gateway** (to expose the Lambda to the frontend).

3.  **Infrastructure as Code (IaC):**
    * Tool: **Terraform**.
    * State Management: Local for now.
    * Structure: We are working specifically in the `/aws` directory of a monorepo that will eventually hold Azure/GCP implementations.

## Development Constraints & Rules
* **No Console Actions:** All infrastructure must be provisioned via Terraform.
* **Cost Aware:** Prioritize AWS Free Tier eligible resources.
* **Security:** strict IAM policies (least privilege), no hardcoded credentials in code.
* **Language:** Python for backend logic, HCL for Infrastructure.