# Muliverse Data Engineering Task

Your objective is to demonstrate your proficiency in managing an ETL pipeline (Extract, Transform, Load) using Python.

You will design a strategy to export data from a sample Multiverse API, transform it, and store it in an S3-based data lake.

## API Details

You can find full documentation for the API by following the process described in the [README](README.md) file.
Once the API is running locally you can view the docs at http://127.0.0.1:8000/docs

### Authentication

The API uses a oauth2 password flow, using the URL, username and password:
URL: http://127.0.0.1:8000/login
Username: multiverse
Passord: mult1v3r53

A successful login with return a token which should be provided as a bearer token in the Authorization header in subsequent requests to authenticated endpoints

### Pagination

Some of the endpoints support pagination. In these cases, a `next_token` will be provided in the `pagination` block in the response.

To retrieve the next set of results, this should be provided in the next request as the value for the `pagination_token` query string parameter.

If there are no further pages, the `next_token` returned will be null.

## Task Requirements

- Design and implement a solution to extract data associated with Apprenticeships, Projects and Programmes.
- Implement necessary transformations to normalize and clean the data as required.
- Write the code to store the transformed data in an S3-based data lake (we understand that you won't be able to test this step without access to AWS)

## Submission:

- Provide the Python scripts in a GitHub repository or as a ZIP file.
- Include a README file with clear instructions on how to set up and run your solution.
- Ensure your code is well-documented and follows best practices.
