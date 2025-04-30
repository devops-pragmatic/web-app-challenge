# DevOps Essentials Web App Challenge

## Objective

In this assignment, you will develop a simple web application using Python and Flask, containerize it with Docker, manage services with Docker Compose, implement a health check, set up a GitHub Actions pipeline to test your application, and version control everything with Git and GitHub. This project aims to provide hands-on experience with key DevOps tools and practices.

### Tasks
1. Develop the Web Application

Create a Flask application with the following routes:
/: Displays a welcome message (e.g., "Welcome to my DevOps app!").
/visit: Increments and displays the number of visits, using Redis to store the count.
/health: Checks the connection to Redis and returns HTTP 200 if successful, otherwise HTTP 500.

Use environment variables REDIS_HOST and REDIS_PORT to configure the Redis connection.
Utilize the redis Python package to interact with Redis.

2. Containerize the Application

Write a Dockerfile to build an image for your Flask application:
Use python:3.9-slim as the base image.
Install dependencies listed in requirements.txt.
Copy the application code into the image.
Expose port 5000.
Set the command to run the Flask application.



3. Manage Services with Docker Compose

Create a docker-compose.yml file to define and manage the following services:
web: Your Flask application, built from the Dockerfile.
redis: The Redis service using the redis:alpine image.


Configure the web service to:
Depend on the redis service.
Use environment variables to connect to Redis (e.g., REDIS_HOST=redis, REDIS_PORT=6379).
Map port 8000 on the host to port 5000 in the container.


Ensure that the Redis service uses a volume to persist data, so the visit count remains across container restarts.
Optionally, add a health check for the web service to verify the /health endpoint.

4. Set Up GitHub Actions Pipeline

Create a GitHub Actions workflow file at .github/workflows/test.yml.
The workflow should trigger on pull requests to the main branch.
Include steps to:
Checkout the repository code.
Build and start the services in detached mode using docker-compose up --build -d.
Wait for the services to start (implement a delay or loop to check readiness).
Verify the /health endpoint returns HTTP 200 by curling http://localhost:8000/health.
Clean up by running docker-compose down.


5. Version Control and Documentation

Initialize a Git repository in your project directory.
Create a .gitignore file to exclude unnecessary files (e.g., __pycache__, .env).
Commit all relevant files with meaningful commit messages.
Write a README.md file that includes:
A brief description of the project.
Instructions on how to build and run the application locally using Docker Compose.
An explanation of the health check and how the GitHub Actions pipeline tests the application.


Push your repository to GitHub and ensure it is public.

### Deliverables

A link to your public GitHub repository containing:
The source code (app.py or similar).
requirements.txt.
Dockerfile.
docker-compose.yml.
.github/workflows/test.yml.
README.md.
.gitignore.


The repository should demonstrate a working Flask application with a persistent visit counter and a functional health check.
The GitHub Actions pipeline should successfully test the application on pull requests.

### Requirements

The application must run correctly within Docker containers.
The visit counter must persist across container restarts, thanks to the Redis volume.
The health check must accurately reflect the connection status to Redis.
The GitHub Actions pipeline must pass, indicating that the application starts correctly and the health check succeeds.

### Resources

Docker Documentation
Docker Compose Documentation
Flask Documentation
Redis-py Documentation
GitHub Actions Documentation

### Example File Structure
project/
├── .github/
│   └── workflows/
│       └── test.yml
├── app.py
├── requirements.txt
├── Dockerfile
├── docker-compose.yml
├── README.md
├── .gitignore

Note: All files should be created by you based on the instructions provided. Use the resources linked above to learn and implement the required components. Do not copy code from external sources; instead, understand the concepts and apply them to your project.
