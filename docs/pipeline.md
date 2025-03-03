# CI/CD Pipeline Process

This document describes the pipeline used for automated deployments.

## ** Pipeline Overview**
The pipeline is built using **CircleCI** and consists of:
1. **Code Checkout** - Pulls the latest code from GitHub.
2. **Install Dependencies** - Installs required Node.js and Angular packages.
3. **Linting & Testing** - Ensures code quality.
4. **Build Application** - Compiles frontend and backend.
5. **Deploy to AWS** - Uploads frontend to S3 and backend to Elastic Beanstalk.

## ** Configuration**
The CI/CD pipeline is configured in `.circleci/config.yml` to do the following:

### Build
1. Install node, npm
    - any other frontend dependencies
    - any other api dependencies
2. Lint frontend
3. Build 
    - build frontend
    - build api

### Hold
- user approve continue

### Deploy
1. install
    - eb, aws
2. deploy app
    - install dependencies
    - build frontend and api
    - run deployment to elastic beanstalk