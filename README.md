# Alzheimer's Risk Prediction using Machine Learning

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## Table of Contents

1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Tech Stack](#tech-stack)
4. [Live Demo](#live-demo)
5. [Installation and Setup](#installation-and-setup)
   - [Backend Setup](#backend-setup)
   - [Frontend Setup](#frontend-setup)
6. [Running the Application](#running-the-application)
   - [Running the Backend](#running-the-backend)
   - [Running the Frontend](#running-the-frontend)
7. [API Endpoints](#api-endpoints)
   - [POST /predict](#post-predict)
   - [GET /feature_importance](#get-feature_importance)
8. [File Structure](#file-structure)
9. [Contributing](#contributing)
10. [License](#license)

## Project Overview

**Alzheimer's Risk Prediction using Machine Learning** is a web application that predicts an individual's risk of developing Alzheimer's disease based on genetic factors. Leveraging advanced machine learning techniques and interactive visualizations, the app provides users with valuable insights into their genetic predisposition.

**Goal of the App**: To empower individuals and healthcare professionals with predictive analytics for early detection and prevention strategies related to Alzheimer's disease.

**Live Demo**: You can try out the application here:

👉 **[Alzheimer's Risk Prediction App](https://alzheimerspredictionfrontend-fbwful15c-sam-boesens-projects.vercel.app/)** 👈

## Features

- **Risk Prediction**: Input genetic data to receive a personalized risk percentage.
- **SHAP Value Explanation**: Visualize feature importance using SHAP (SHapley Additive exPlanations) values.
- **Risk Breakdown**: Detailed analysis of how each genetic factor contributes to the overall risk.

## Tech Stack

- **Frontend**:
  - [React](https://reactjs.org/)
  - [Material-UI](https://material-ui.com/)
- **Backend**:
  - [Flask](https://flask.palletsprojects.com/)
  - [Python](https://www.python.org/)
  - [XGBoost](https://xgboost.readthedocs.io/)
  - [Google Cloud Storage](https://cloud.google.com/storage)
- **Deployment**:
  - [Vercel](https://vercel.com/) (Frontend)
  - [Google Cloud Run](https://cloud.google.com/run) (Backend)
- **Containerization**:
  - [Docker](https://www.docker.com/)

## Live Demo

Experience the application live without any setup:

👉 **[Alzheimer's Risk Prediction App](https://alzheimerspredictionfrontend-fbwful15c-sam-boesens-projects.vercel.app/)** 👈

## Installation and Setup

If you'd like to run the application locally or explore the code further, follow these instructions.

### Backend Setup

#### Prerequisites

- **Python 3.8+**
- **pip** package manager
- **Google Cloud Account** (for accessing the machine learning model)
- **Git**

### Frontend Setup

#### Prerequisites

- **Node.js v14+**
- **npm or yarn** package manager
- **Google Cloud Account** (for accessing the machine learning model)
- **Git**

#### Steps

1. **Clone the Repository**

   ```bash
   git clone https://github.com/yourusername/alzheimers-risk-prediction.git
   cd alzheimers-risk-prediction/backend
   
2. **Create a Virtual Environment**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate

3. **Install depndecies**

   ```bash
   pip install -r requirements.txt

4. **Set Environment Variables**

   ```bash
   export GOOGLE_APPLICATION_CREDENTIALS="/path/to/your/service-account-key.json"
   export BUCKET_NAME="your-google-cloud-bucket-name"
   export PIPELINE_FILENAME="your_risk_model.joblib"
   export LOCAL_PIPELINE_PATH="/app/models/your_risk_model.joblib"

5. **Start the Backend server**

   ```bash
   flask run --host=0.0.0.0 --port=8080

**Note**:

- Replace `/path/to/your/service-account-key.json` with the actual path to your Google Cloud service account key JSON file.
- Update `your-google-cloud-bucket-name` with the name of your Google Cloud Storage bucket.
- Ensure that the `your_risk_model.joblib` file is correctly placed in the specified `LOCAL_PIPELINE_PATH`.

### Running the Application

### Running the Backend

#### Without Docker

If you want to test Backend locally without using Docker you can do so using tools like:
- **cURL**: A command-line tool for transferring data with URLs. It's typically pre-installed on Unix-based systems. [Download cURL](https://curl.se/download.html) if it's not available.
- **Postman**: A graphical tool for API development. [Download Postman](https://www.postman.com/downloads/) if you prefer a GUI.

 #### With Docker

When you are ready to deploy you should use a Docker image to containerize the application

1. **Build the Docker image**

   ```bash
   docker build -t alzheimers-backend .

2. **Run the Docker container**

   ```bash
   docker run -p 8080:8080 \
   e GOOGLE_APPLICATION_CREDENTIALS="/app/credentials/service-account-key.json" \
   v /path/to/your/service-account-key.json:/app/credentials/service-account-key.json \
   alzheimers-backend

### Running the Frontend

The frontend for this we app was deployed on vercel which will explained below. It is also important to note that local testing is often an important part of the devlopment process as well so that will be documnented as well:

#### Without Docker

If you prefer to run the frontend locally without using Docker, follow these steps:

1. **Navigate to the Frontend Directory**

   Ensure you're in the `frontend` directory of the project.

   ```bash
   cd frontend

2. **Install depnedencies**

   ```bash
   npm install
   # or
   yarn install

3. **Configure Environment Variables**

   Create a .env file in the frontend directory to store environment variables.

   ```bash
   Copy code
   touch .env
   
   # Open the .env file in your preferred text editor and add the following

   env
   Copy code
   REACT_APP_BACKEND_URL="http://localhost:8080"

 Note: Replace http://localhost:8080 with the actual URL of your backend server if it's hosted elsewhere.
 Note 2.0: This is really only usefull during local testing and devlopment. Cloud deployment should be done 
 using docker


#### Deploying the Frontend via Vercel

While running the frontend locally is essential for development and testing, deploying it to a cloud platform like Vercel ensures scalability, reliability, and easy access for users. Vercel is an excellent choice for deploying React applications due to its seamless integration and automatic optimizations.

Here’s a quick guide to deploying your frontend application on Vercel:

1. **Prerequisites**

   - **Vercel Account**: If you don't have one, sign up for free at [Vercel](https://vercel.com/signup).
   - **GitHub Repository**: Ensure your frontend code is pushed to a GitHub repository. Vercel integrates seamlessly with GitHub for continuous deployments.

2. **Connect Your GitHub Repository to Vercel**

   1. **Login to Vercel**

      Navigate to [Vercel](https://vercel.com/) and log in to your account.

   2. **Import Project**

      - Click on the **"New Project"** button.
      - Select **"Import Git Repository"**.
      - Choose the GitHub repository containing your frontend code. If prompted, authorize Vercel to access your GitHub account.

3. **Configure Project Settings**

   During the import process, Vercel will auto-detect the framework (e.g., React). Review and configure the following settings:

   - **Framework Preset**: Ensure it correctly identifies your framework (e.g., React).
   - **Build Command**: Typically, `npm run build` or `yarn build`.
   - **Output Directory**: Usually `build` for React applications.

4. **Set Environment Variables**

   Environment variables are crucial for connecting the frontend to the backend. To set them up:

   1. **Navigate to Project Settings**

      After importing the project, go to your project dashboard on Vercel and click on **"Settings"**.

   2. **Add Environment Variables**

      - Click on **"Environment Variables"** in the sidebar.
      - Add the following variables:

        | Name                   | Value                         |
        |------------------------|-------------------------------|
        | `REACT_APP_BACKEND_URL` | `https://your-backend-url.com` |

      **Note**: Replace `https://your-backend-url.com` with the actual URL of your deployed backend server.

5. **Deploy the Project**

   - After configuring the settings and environment variables, click on **"Deploy"**.
   - Vercel will start building and deploying your project. This process may take a few minutes.
   - Once deployed, Vercel provides a live URL for your application, typically in the format `https://your-project-name.vercel.app/`.

6. **Enable Automatic Deployments**

   Vercel supports automatic deployments, meaning every time you push changes to the connected GitHub repository, Vercel will automatically rebuild and deploy the updated frontend.

   **Benefits**:
   - **Continuous Integration**: Ensures that your live application is always up-to-date with the latest code changes.
   - **Easy Rollbacks**: If a deployment introduces issues, Vercel allows you to rollback to previous deployments effortlessly.

7. **Accessing Your Deployed Application**

   Once the deployment is complete, you can access your live frontend application via the URL provided by Vercel (e.g., `https://your-project-name.vercel.app/`).

8. **Optional: Configure a Custom Domain**

   If you have a custom domain, you can link it to your Vercel project for a more professional appearance.

   1. **Add Domain in Vercel**

      - In your project dashboard on Vercel, navigate to the **"Domains"** section.
      - Click on **"Add"** and enter your custom domain name.

   2. **Update DNS Settings**

      - Vercel will provide DNS records that you need to add to your domain registrar.
      - Follow the instructions to update your DNS settings accordingly.

   3. **Verify Domain**

      - After updating DNS settings, Vercel will verify the domain. This may take some time depending on DNS propagation.

#### Quick Setup Summary

1. **Push your frontend code to GitHub.**
2. **Connect your GitHub repository to Vercel.**
3. **Configure build settings and environment variables in Vercel.**
4. **Deploy the project and access it via the provided URL.**

**Note**: This guide provides a high-level overview. For more detailed instructions, refer to the [Vercel Documentation](https://vercel.com/docs).
