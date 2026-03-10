Dockerized Flask App with CI/CD 🚀

This project demonstrates how to build, test, containerize, and automatically publish a Flask application using Docker and GitHub Actions CI/CD.

The pipeline automatically runs tests and builds a Docker image whenever code is pushed to the main branch.

Project Overview

This project contains a simple Flask application that returns:

Hello, World!

The application is:

Containerized using Docker

Tested using Pytest

Automatically built and pushed to Docker Hub

Automated using GitHub Actions CI/CD

Project Structure
Docker_CICD/
│
├── .github/
│   └── workflows/
│       └── cicd.yml          # CI/CD pipeline configuration
│
├── app.py                    # Flask application
├── test_app.py               # Pytest test case
├── requirements.txt          # Python dependencies
├── DockerFile                # Docker configuration
├── .gitignore
└── README.md
Flask Application

The application exposes a single endpoint.

Route
GET /
Response
Hello, World!

Example code:

from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
    return "Hello, World!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
Running the Application Locally
Install dependencies
pip install -r requirements.txt
Run the Flask server
python app.py

Open in browser:

http://localhost:5000

Expected output:

Hello, World!
Running Tests

The project uses Pytest to test the API.

Run tests with:

pytest

Example test:

from app import app

def test_hello_world():
    response = app.test_client().get('/')
    assert response.status_code == 200
    assert response.data == b'Hello, World!'
Docker Setup

This project uses Docker to containerize the Flask application.

Build Docker Image
docker build -t flask-cicd-app .
Run Docker Container
docker run -p 5000:5000 flask-cicd-app

Open:

http://localhost:5000
Dockerfile Explanation

Key steps in the Dockerfile:

Use lightweight Python image

Set working directory

Copy application files

Install dependencies

Expose port

Run the application

Example:

FROM python:3.10-slim

WORKDIR /app

COPY . /app

RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 5000

CMD ["python", "app.py"]
CI/CD Pipeline (GitHub Actions)

The CI/CD workflow automatically performs the following steps:

1️⃣ Checkout repository
2️⃣ Install Python dependencies
3️⃣ Run Pytest tests
4️⃣ Build Docker image
5️⃣ Login to DockerHub
6️⃣ Push image to DockerHub

Workflow file:

.github/workflows/cicd.yml

The pipeline triggers on:

push to main
pull requests to main
Required GitHub Secrets

To push images to DockerHub, add these repository secrets:

DOCKER_USERNAME
DOCKER_PASSWORD

Where:

DOCKER_USERNAME = DockerHub username

DOCKER_PASSWORD = DockerHub access token

DockerHub Image

After successful CI/CD execution, the Docker image will be available at:

dockerhub_username/flask-cicd-app:latest

Example:

docker pull username/flask-cicd-app:latest
Key Technologies Used

Python

Flask

Docker

Pytest

GitHub Actions

CI/CD

