\# Node.js DevOps App — Dockerized



A minimal Node.js/Express application, containerized following DevOps best practices as part of a hands-on DevOps portfolio.



Docker Hub: https://hub.docker.com/r/rohanqamar/nodejs-devops-app



\## What this demonstrates



\- Multi-stage Docker build (separate build and runtime stages) to keep the final image lean

\- Alpine-based image - final image size \~49MB vs 900MB+ for a full node base image

\- Non-root container user for security (no process runs as root inside the container)

\- Built-in HEALTHCHECK so orchestrators (Docker, Kubernetes) can detect if the app is actually serving traffic, not just running

\- Layer-caching-aware Dockerfile ordering (dependencies copied/installed before source code, so code changes don't invalidate the dependency install cache)

\- Versioned image tags (v1, not just latest) for reproducible deployments



\## Run it yourself



No Node.js installation required, just Docker:



&#x20;   docker pull rohanqamar/nodejs-devops-app:v1

&#x20;   docker run -d -p 3000:3000 --name nodejs-devops-app rohanqamar/nodejs-devops-app:v1



Then visit:

\- http://localhost:3000 - main endpoint

\- http://localhost:3000/health - health check endpoint



\## Run from source



&#x20;   npm install

&#x20;   npm start



\## Build the image yourself



&#x20;   docker build -t nodejs-devops-app .



\## Tech stack



Node.js, Express, Docker (multi-stage builds, Alpine Linux)

