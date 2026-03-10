# Dockerized Flask App with CI/CD 🚀

This project demonstrates how to build, test, containerize, and automatically publish a Flask application using **Docker** and **GitHub Actions CI/CD**.

The pipeline automatically runs tests and builds a Docker image whenever code is pushed to the main branch.

---

# Project Overview

This project contains a simple Flask application that returns:

The application is:

- Containerized using **Docker**
- Tested using **Pytest**
- Automatically built and pushed to **Docker Hub**
- Automated using **GitHub Actions CI/CD**

---

# Project Structure
Docker_CICD/
│
├── .github/
│ └── workflows/
│ └── cicd.yml # CI/CD pipeline configuration
│
├── app.py # Flask application
├── test_app.py # Pytest test case
├── requirements.txt # Python dependencies
├── DockerFile # Docker configuration
├── .gitignore
└── README.md

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