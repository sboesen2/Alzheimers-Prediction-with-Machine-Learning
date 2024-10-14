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

#### Steps

1. **Clone the Repository**

   ```bash
   git clone https://github.com/yourusername/alzheimers-risk-prediction.git
   cd alzheimers-risk-prediction/backend
