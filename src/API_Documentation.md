# API Documentation

## Overview

This documentation provides an overview of the FastAPI application located in the `src/API` folder. FastAPI is a modern, fast (high-performance) web framework for building APIs with Python 3.7+ based on standard Python type hints.

## Table of Contents

- [API Documentation](#api-documentation)
  - [Overview](#overview)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [Project Structure](#project-structure)
  - [API Endpoints](#api-endpoints)
    - [Users](#users)
      - [Create User](#create-user)
      - [Get User](#get-user)
    - [Items](#items)
      - [Create Item](#create-item)
      - [Get Item](#get-item)
  - [Running the Application](#running-the-application)

## Installation

To set up the FastAPI application using Poetry, follow these steps:

1. **Install Poetry** if you haven't already. You can follow the instructions from the [Poetry official documentation](https://python-poetry.org/docs/#installation).

2. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

3. Install the dependencies using Poetry:

    ```
    bash
    poetry install
    ```
This command will install all the required dependencies specified in the `pyproject.toml` file.

To activate the virtual environment created by Poetry, use:

    ```
    bash
    poetry shell
    ```
This command will activate the virtual environment.

## Project Structure

The project structure of the FastAPI application is as follows:
    ```

    /API
    ┣ .vscode/
    ┃ ┣ launch.json
    ┃ ┗ settings.json
    ┣ Docs/
    ┃ ┗ API_Documentation.md
    ┣ __pycache__/
    ┃ ┣ __init__.cpython-39.pyc
    ┃ ┗ index.cpython-39.pyc
    ┣ app/
    ┃ ┣ data/
    ┃ ┃ ┗ voice_responses/
    ┃ ┃   ┣ runtime_reponse.xml
    ┃ ┃   ┗ runtime_response.xml
    ┃ ┣ helpers/
    ┃ ┃ ┣ __init__.py
    ┃ ┃ ┗ get_version.py
    ┃ ┣ services/
    ┃ ┃ ┣ __init__.py
    ┃ ┃ ┣ dynamo.py
    ┃ ┃ ┣ graph_service.py
    ┃ ┃ ┣ secret_manager.py
    ┃ ┃ ┣ twilio_service.py
    ┃ ┃ ┗ user_service.py
    ┃ ┣ __init__.py
    ┃ ┣ app_version
    ┃ ┗ index.py
    ┣ Dockerfile
    ┣ __init__.py
    ┣ deploy.sh
    ┣ open_api_spec.json
    ┣ poetry.lock
    ┣ pyproject.toml
    ┗ requirements.txt
    ```
## API Endpoints

### Users
#### Create User

**Endpoint**: POST /users/
**Description**: Create a new user.
**Request Body**:
    ```
    json
    {
    "username": "string",
    "email": "string",
    "full_name": "string"
    }
    ```
**Response**:201 Created
    ```
    json
    {
    "id": "integer",
    "username": "string",
    "email": "string",
    "full_name": "string"
    }
    ```
#### Get User

**Endpoint**: GET /users/{user_id}
**Description**: Retrieve a user by ID.
**Response**:
- 200 OK
    ```
    json
    {
    "id": "integer",
    "username": "string",
    "email": "string",
    "full_name": "string"
    }
    ```

- 404 Not Found if user does not exist.

### Items
#### Create Item

**Endpoint**: POST /items/
**Description**: Create a new item.
**Request Body**:
    ```
    json
    {
    "name": "string",
    "description": "string",
    "price": 0.0
    }
    ```
**Response**:
- 201 Created
    ```
    json
    {
    "id": "integer",
    "name": "string",
    "description": "string",
    "price": 0.0
    }
    ```
#### Get Item

**Endpoint**: GET /items/{item_id}
**Description**: Retrieve an item by ID.
**Response**:
- 200 OK
    ```
    json
    {
    "id": "integer",
    "name": "string",
    "description": "string",
    "price": 0.0
    }
    ```

- 404 Not Found if item does not exist.

## Running the Application

To run the FastAPI application, use the following command within the Poetry environment:

    ```
    bash
    uvicorn main:app --reload
    ```
The application will be available at http://127.0.0.1:8000.
You can access the interactive API documentation at http://127.0.0.1:8000/docs.

 You can add development dependencies using Poetry with the following command:

    ```
    bash
    poetry add --dev pytest
    ```