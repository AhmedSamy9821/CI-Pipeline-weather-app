---
# CI Pipeline with GitHub Actions

## Overview

This project demonstrates a Continuous Integration (CI) pipeline using **GitHub Actions** to automate the build and push of Docker images for an application consisting of three services:
- **UI**: Frontend of the application.
- **Auth**: Service for authentication.
- **Weather**: Backend service for weather-related functionality.

The Docker images are pushed to a **Docker Hub registry**.

---

## Features

- **Automated CI Pipeline**: The pipeline is triggered automatically on any push or pull request to the `main` branch.
- **Secrets Management**: Sensitive information like Docker Hub username and token are securely stored in **GitHub Secrets**.
- **Dockerized Services**: Builds Docker images for three services: UI, Auth, and Weather.
- **Reusable Actions**:
  - `actions/checkout@v3`: Checks out the repository code.
  - `docker/login-action@v3`: Logs into Docker Hub securely.

---

## Workflow Trigger

The pipeline is triggered on:
1. **Push**: Any code changes pushed to the `main` branch.
2. **Pull Request**: Any pull request targeting the `main` branch.

---

## Workflow Steps

The CI pipeline consists of the following steps:

1. **Checkout Repository**:
   - Uses the `actions/checkout@v3` action to fetch the repository code.

2. **Login to Docker Hub**:
   - Uses `docker/login-action@v3` to authenticate with Docker Hub using secrets.

3. **Build Docker Images**:
   - Builds separate Docker images for:
     - `UI`
     - `Auth`
     - `Weather`

4. **Push Docker Images to Docker Hub**:
   - Pushes the Docker images to the specified Docker Hub repository.

---

## Secrets Configuration

To securely store your Docker credentials:
1. Go to your repository on GitHub.
2. Navigate to **Settings → Secrets and variables → Actions → New repository secret**.
3. Add the following secrets:
   - `DOCKERHUB_USERNAME`: Your Docker Hub username.
   - `DOCKERHUB_TOKEN`: Your Docker Hub token or password.

---

## How to Use

1. Clone this repository:
   ```bash
   git clone <[repository-url](https://github.com/AhmedSamy9821/CI-Pipeline-weather-app.git)>
   ```

2. Add your Docker credentials to **GitHub Secrets** as described above.

3. Make changes to any service (UI, Auth, Weather) and push to the `main` branch or create a pull request. The pipeline will automatically build and push updated Docker images.

---

## Results

- The Docker images for the three services will be available in your Docker Hub repository after the pipeline completes.
- You can pull the images using:
  ```bash
  docker pull <docker_username>/<service_name>:latest
  ```

---
