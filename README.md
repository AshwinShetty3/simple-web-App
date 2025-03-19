# Automating the deployment of a simple web application

This is a simple web application that displays "Hello, DevOps!". The project includes a CI/CD pipeline using GitHub Actions to automatically build and deploy the application.

## Prerequisites

- Docker
- nginx
- Git
- GitHub account

## Project Structure
The repository contains the following key files:
```bash
simple-web-app-devops/
├── .github/
│   └── workflows/
│       └── ci-cd.yml    # GitHub Actions workflow
├── index.html           # web page
├── Dockerfile           # Docker container configuration
└── README.md            # Documentation
   ```
## Setup

1. Clone the Repository:

```bash
https://github.com/AshwinShetty3/simple-web-app-devops.git
cd simple-web-app-devops
   ```

2. Building and Running Locally with Docker:

```bash
 # Build the Docker image
docker build -t simple-web-app .

# Run the container
docker run -p 8080:80 simple-web-app

   ```

3. Exposed the Port to Mappe your application to port 8080 
```bash
 In EC2 → Security Groups → Add a new rule →  Type: Custom TCP → Source: 0.0.0.0/0 (or
 limit to specific IPs for better security)
   ```

4. Verify Your Application is Running on Port 8080:
 ```bash
# Eg: abc123def456   your-web-app  "nginx -g 'daemon of…"   5 minutes ago  Up 5 minutes  0.0.0.0:8080->80/tcp   web-app
 docker ps
   ```
   
5. Access the application in your browser:

```bash
 http://<your-ec2-public-ip>:8080
or
 http://localhost:8080
   ```
   

## This project uses GitHub Actions to automate the build and deployment process.:
The CI/CD pipeline is defined in .github/workflows/ci-cd.yml. It performs the following steps:

1. The pipeline performs the following steps:
   - Checkout Code: Fetches the latest code from the repository
   - HTML Validation: Checks the syntax of the HTML file
   - Docker Build: Builds the Docker image
   - Run Docker Container: Runs the Docker container locally

2. The pipeline is triggered automatically on:
   - Push to main branch
   - Pull requests to main branch


## Making Changes and Triggering the CI/CD Pipeline:

1. To Test the CI/CD Pipeline Make Changes or Edit the index.html file locally then Commit and push the changes:

```bash
# Stage your changes
git add .

# Commit your changes
git commit -m "Your descriptive commit message"

# Push to GitHub to trigger the CI/CD pipeline
git push origin main
  ```
2. Verify the Pipeline:

```bash
 - Go to the "Actions" tab in your GitHub repository
 - Check that the pipeline runs automatically after the push
 - Verify that the new changes are deployed and reflected in your web app
  ```

## To Enable Notifications (on failures):
   1. Go to your GitHub repository.
   2. Click on Settings → Notifications.
   3. Under Custom routing, ensure your email is added.
   4. Scroll down to Actions and enable notifications for:
      Workflow runs (failures only).
      Workflow jobs (failures only).


     

