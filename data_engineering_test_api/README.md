# Multiverse Data Engineering Task API

This is a FastAPI web application that implements an API for the Multiverse data engineer task.

The application includes endpoints for apprenticeships, projects, and programmes, and uses OAuth2 for authentication.

## Features

- OAuth2 authentication
- Endpoints for apprenticeships, projects, and programmes
- Once running, Swagger documentation will be available at `http://localhost:8000/docs`

## Setup and Run

### Prerequisites

- Python 3.7+
- pip (Python package installer)

### Installation

1. Navigate to the this folder in a terminal,:

   ```sh
   cd ~/Documents/mv_data_engineering/
   ```

2. Create a virtual environment and activate it:

   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

3. Install the required dependencies:

   ```sh
   pip install -r requirements.txt
   ```

4. Start the FastAPI application:

   ```sh
   uvicorn app:app --reload
   ```

5. Access the Swagger documentation at http://localhost:8000/docs.
