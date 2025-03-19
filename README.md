# Automating the deployment of a simple web application

This is a simple web application that displays "Hello, DevOps!". The project includes a CI/CD pipeline using GitHub Actions to automatically build and deploy the application.

## Prerequisites

- Docker
- nginx
- Git
- GitHub account

## Setup

1. Pull form Docker Hub or Clone this repository:

```bash
https://github.com/AshwinShetty3/DevOps-Assignment.git
   ```

2. Build the Docker Image:

```bash
 docker build -t simple-web-app .
   ```

3. Exposed the Port:
   Mappe your application to port 8080 (you can use any port number instead of 8080)
```bash
 docker build -t simple-web-app .
   ```

4. Verify Your Application is Running on Port 8080:
   Eg: abc123def456   your-web-app  "nginx -g 'daemon of…"   5 minutes ago  Up 5 minutes  0.0.0.0:8080->80/tcp   web-app
 ```bash
 docker ps
   ```
   
5. Test Your Application:

```bash
 http://<your-ec2-public-ip>:8080
   ```
   

## CI/CD Pipeline using GitHub Actions Workflow setup:

This project uses GitHub Actions to automate the build and deployment process. The pipeline performs the following steps:
The CI/CD pipeline is defined in .github/workflows/ci-cd.yml. It performs the following steps:

1. Checkout Code: Fetches the latest code from the repository.
2. Validate HTML Syntax: Checks the index.html file for syntax errors.
3. Build Docker Image: Builds the Docker image.
4. Run Docker Container: Runs the Docker container locally.

1. Push the web-app to your repository:

```bash
git init
git add .
git commit -m "Your commit message"
git push origin main
  ```

## Test the CI/CD Pipeline:

1. Make Changes or Edit the index.html file locally. For example, change "Hello, DevOps!" to "Hello, CI/CD!".
   Commit and push the changes:

```bash
git add index.html
git commit -m "Update index.html message"
git push origin main
  ```
2. Verify the Pipeline:
   Go to the "Actions" tab in your GitHub repository.
   Check that the pipeline runs automatically after the push.
   Verify that the new changes are deployed and reflected in your web app.

## To Monitor the Pipeline:
   Set up monitoring to ensure the pipeline runs smoothly in the future.

1. Enable Notifications:
   - In your GitHub repository, go to Settings → Notifications.
   1. Go to your GitHub repository.
   2. Click on Settings → Notifications.
   3. Under Custom routing, ensure your email is added.
   4. Scroll down to Actions and enable notifications for:
     - Workflow runs (failures only).
     - Workflow jobs (failures only).

2. Check Pipeline Logs:
   - Regularly review the logs in the "Actions" tab to ensure there are no errors.

##  Additional addons: 
   To enhance further Improve the CI/CD pipeline:
   
```bash
Add Testing: Add a step to run automated tests (like: unit tests, integration tests) in the pipeline.
Add Linting: Use a linter for HTML to enforce code quality.
Add Security Scanning: Use tools like 'trivy' or 'snyk' to scan your Docker image for vulnerabilities.
   ```
     

