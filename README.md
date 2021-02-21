# Project IaC Recipe

This recipe is an Infrastructure as Code (IaC) recipe for deploying cloud 
projects in Google Cloud Platform (GCP). It demonstrates how to set up an 
Infrastructure-as-Code project with GitHub Actions, and includes a couple 
workflows:

- [review workflow](./.github/workflows/review.yaml)
- [release workflow](./.github/workflows/release.yaml)

## Setup

In this case, using Terraform requires some preconfiguration:

1. Cloud Storage bucket (to serve as the Terraform backend)
2. an authorized service account in IAM with access to the bucket

<sub>Hint: See the
[Project Preconfiguration IaC Recipe](https://github.com/SLIB53/project-preconfiguration-iac-recipe)
for how to perform the preconfiguration using Terraform.</sub>

The GitHub Actions workflows require the following environment variables:

| Secret Name             | Description                                                                                           |
| ----------------------- | ----------------------------------------------------------------------------------------------------- |
| GCP_PROJECT_ID          | The GCP Project ID of the target project for deployment                                               |
| GCP_SA_KEY              | The GCP IAM credentials used to authenticate and authorize GitHub Actions (use base64 encoded JSON)   |
| GCS_BACKEND_BUCKET_NAME | The name of the bucket used to store the tfsate (passed into the "bucket" parameter of a gcs backend) |
