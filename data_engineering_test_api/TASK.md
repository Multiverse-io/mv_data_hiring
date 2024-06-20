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

## Submission

- Provide the Python scripts in a GitHub repository or as a ZIP file.
- Include a README file with clear instructions on how to set up and run your solution.
- Ensure your code is well-documented and follows best practices.

## Submission Options

### Option 1: Submit via Forking and Pull Request

1. **Fork and Clone**:
   - Fork this repository to your GitHub account.
   - Clone your fork to your local machine:

     ```sh
     git clone git@github.com:YOUR_USERNAME/mv_data_hiring.git
     ```

2. **Complete the tasks**:
   - Follow the instructions provided in the relevant files and directories.

3. **Push and PR**:
   - Push your changes to your forked repository:

     ```sh
     git add .
     git commit -m "Complete data test"
     git push origin main
     ```

   - Create a Pull Request (PR) to the original repository with a description of your approach.

### Option 2: Submit via Email

1. **Download and Complete**:
   - Download the repository as a zip file from GitHub.
   - Extract the zip file and complete the tasks.

2. **Prepare and Send**:
   - Zip your completed work.
   - Email the zipped file to [your_email@example.com] with a description of your approach.