# Kubernetes Simple Demo Deployment Guide

[![Docker Image](https://img.shields.io/docker/pulls/amirhaytham/flask-k8s-demo?label=Docker%20Pulls&style=flat-square&cacheSeconds=60)](https://hub.docker.com/r/amirhaytham/flask-k8s-demo)
[![Kubernetes Deployment](https://img.shields.io/badge/Kubernetes-Deployment%20Ready-brightgreen?style=flat-square)](https://kubernetes.io/)
[![Python Version](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)
[![Build Status](https://img.shields.io/github/actions/workflow/status/AmirHaytham/flask-k8s-demo/python-package-conda.yml?branch=main&label=Build%20Status&style=flat-square)](https://github.com/AmirHaytham/flask-k8s-demo/actions)
[![Contributors](https://img.shields.io/github/contributors/AmirHaytham/flask-k8s-demo?style=flat-square)](#contributing)
[![Code Size](https://img.shields.io/github/languages/code-size/AmirHaytham/flask-k8s-demo?style=flat-square)](https://github.com/AmirHaytham/flask-k8s-demo)
[![Open Issues](https://img.shields.io/github/issues/AmirHaytham/flask-k8s-demo?label=Issues&style=flat-square)](https://github.com/AmirHaytham/flask-k8s-demo/issues)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen?style=flat-square)](#contributing)

## Table of Contents

- [About the Project](#about-the-project)
- [Built With](#built-with)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the Application](#running-the-application)
- [Deployment](#deployment)
  - [Dockerizing the Application](#dockerizing-the-application)
  - [Pushing the Docker Image](#pushing-the-docker-image)
  - [Creating Kubernetes Deployment](#creating-kubernetes-deployment)
  - [Exposing the Deployment](#exposing-the-deployment)
- [File Structure](#file-structure)
- [Contributing](#contributing)
- [License](#license)

## About the Project

This project demonstrates the deployment of a simple web application on Kubernetes. The application is a basic "Hello World" web server built with Python and Flask, containerized using Docker, and deployed on a Kubernetes cluster.

## Built With

- [Python](https://www.python.org/)
- [Flask](https://flask.palletsprojects.com/)
- [Docker](https://www.docker.com/)
- [Kubernetes](https://kubernetes.io/)

## Getting Started

To get a local copy up and running, follow these steps.

### Prerequisites

Ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Kubernetes](https://kubernetes.io/docs/setup/) (Minikube or Docker Desktop)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

### Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/AmirHaytham/flask-k8s-demo.git
   ```

2. **Navigate to the project directory:**

   ```bash
   cd flask-k8s-demo
   ```

3. **Create a virtual environment and activate it:**

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

4. **Install the required packages:**

   ```bash
   pip install -r requirements.txt
   ```

### Running the Application

To run the application locally:

```bash
python app.py
```

The application will be accessible at `http://localhost:5000`.

## Deployment

### Dockerizing the Application

1. **Build the Docker image:**

   ```bash
   docker build -t flask-k8s-demo .
   ```

2. **Run the Docker container locally (optional):**

   ```bash
   docker run -p 5000:5000 flask-k8s-demo
   ```

   Access the application at `http://localhost:5000`.

### Pushing the Docker Image

1. **Log in to Docker Hub:**

   ```bash
   docker login
   ```

2. **Tag and push the image:**

   ```bash
   docker tag flask-k8s-demo amirhaytham/flask-k8s-demo:latest
   docker push amirhaytham/flask-k8s-demo:latest
   ```

### Creating Kubernetes Deployment

1. **Apply the deployment configuration:**

   ```bash
   kubectl apply -f deployment.yaml
   ```

2. **Verify the deployment:**

   ```bash
   kubectl get deployments
   ```

   Ensure the deployment is running with the desired number of replicas.

### Exposing the Deployment

1. **Expose the deployment as a service:**

   ```bash
   kubectl expose deployment hello-world-deployment --type=LoadBalancer --port=80 --target-port=5000
   ```

2. **Retrieve the external IP:**

   ```bash
   kubectl get services
   ```

   Once an external IP is assigned, access the application via the provided IP address.

## File Structure

```
flask-k8s-demo/
├── app.py
├── Dockerfile
├── requirements.txt
├── deployment.yaml
├── README.md
└── screenshots/
    └── app_screenshot.png
```

## Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

Distributed under the MIT License. See `LICENSE` for more information.
