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
11. [Contact Author](#contact-author)


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

## API Endpoints

### POST `/predict`

**Description**: Accepts genetic data and returns a predicted Alzheimer's risk percentage.

- **Request URL**: `http://localhost:8080/predict`

- **Request Headers**: Body and Response

  ```http
  Content-Type: application/json

   {
  "snpRiskAllele": "rs12345-A",
  "pValue": 0.001,
  "orBeta": 1.5,
  "riskAlleleFrequency": 0.3,
  "pValueMlog": 3.0
   }
  
  {
  "risk": 78.5,
  "timestamp": "2024-10-14T12:00:00Z"
  }

### GET `/feature_importance`

**Description**: Returns data used to visualize feature importance via SHAP values.

- **Request URL**: `http://localhost:8080/feature_importance`

```json
{
  "feature_importance": {
    "snpRiskAllele": 0.4,
    "pValue": 0.3,
    "orBeta": 0.2,
    "riskAlleleFrequency": 0.1,
    "pValueMlog": 0.05
  }
}

```
## File Structure

The project is organized into several key directories and files to maintain a clean and efficient workflow. Below is an overview of the directory structure:

```plaintext
Alzheimers-Prediction-with-Machine-Learning/
├── backend/
├── frontend/
├── Notebooks/
├── LICENSE
├── README.md
└── .gitignore


---
```

### **Explanation of the Sections:**

1. **File Structure**:
   - **Plaintext Directory Tree**: Provides a visual representation of the project's main directories and files.

2. **Directory Breakdown**:
   - **backend/**:
     - **Description**: Offers a high-level overview of what the backend directory contains and its role in the project.
   - **frontend/**:
     - **Description**: Details the contents and purpose of the frontend directory, highlighting its connection to Vercel and the backend.
   - **Notebooks/**:
     - **Description**: Explains the purpose of the Jupyter notebooks within the project, emphasizing their role in data analysis and model evaluation.
   - **LICENSE**:
     - **Description**: Mentions the licensing of the project.
   - **README.md**:
     - **Description**: Indicates that this documentation file provides an overview and instructions.
   - **.gitignore**:
     - **Description**: States the purpose of the gitignore file in managing version control.

3. **Additional Notes**:
   - **Customization**: Encourages users to adjust the descriptions to better fit their actual project structure.
   - **Sensitive Information**: Reminds users to handle sensitive data securely.

---

### **Customization Tips:**

- **Accurate Descriptions**: Make sure the descriptions for each directory accurately reflect their contents and roles within your project.
  
- **Additional Directories**: If your project contains other directories (e.g., `docs/`, `scripts/`, `tests/`), consider adding them with appropriate descriptions.

- **Visual Enhancements**: You can enhance the directory tree with more detailed subdirectories if needed, but since you prefer a high-level overview, the current structure should suffice.

### **Final Note:**

Ensure that all paths and descriptions are accurate and correspond to your project's actual setup. This high-level overview will help contributors and users understand the organization of your project quickly and navigate it efficiently.

Feel free to reach out if you need further assistance or additional sections for your `README.md`!

## Contributing

I appreciate your interest in contributing to the **Alzheimer's Risk Prediction using Machine Learning** project! Your contributions help enhance the project, improve its functionality, and ensure its continued success. Below are the guidelines and steps to help you get started.

### How to Contribute

#### Reporting Issues

If you encounter any bugs or have ideas for improvements, please [open an issue](https://github.com/yourusername/Alzheimers-Prediction-with-Machine-Learning/issues) in the repository. When reporting an issue, please include:

- A clear and descriptive title.
- A detailed description of the problem or suggestion.
- Steps to reproduce the issue, if applicable.
- Any relevant screenshots or logs.

#### Suggesting Enhancements

I welcome suggestions for new features or enhancements. To propose an improvement:

1. Open an issue in the repository.
2. Provide a clear and descriptive title.
3. Outline the proposed changes and their benefits.
4. Include any relevant examples or references.

#### Submitting Pull Requests

Pull requests (PRs) are the best way to propose changes to the project. By submitting a PR, you are suggesting modifications and additions to the codebase.

1. **Ensure the project is up-to-date**: Sync your fork with the latest changes from the main repository to avoid merge conflicts.
2. **Follow the development workflow**: Refer to the [Development Workflow](#development-workflow) section below.
3. **Provide a clear description**: In your PR, describe what changes you have made and why they are necessary.
4. **Reference issues**: If your PR addresses an existing issue, mention it by including `Closes #issue_number` in your PR description.

### Development Workflow

Follow these steps to contribute effectively:

#### Fork the Repository

1. Navigate to the [Alzheimer's Risk Prediction](https://github.com/yourusername/Alzheimers-Prediction-with-Machine-Learning) repository on GitHub.
2. Click the **Fork** button at the top right to create your own fork of the project.

#### Clone Your Fork

Clone the forked repository to your local machine using Git:

```bash
git clone https://github.com/yourusername/Alzheimers-Prediction-with-Machine-Learning.git
cd Alzheimers-Prediction-with-Machine-Learning

```
#### Create a new branch

```bash
git checkout -b feature/your-feature-name

```
#### Commit your changes
```bash
git add .
git commit -m "Add feature: Brief description of your feature"

```
#### Push toyour fork

```bash
git push origin feature/your-feature-name

```
#### Open a pull request
1. Navigate to your forked repository on GitHub.
2. Click the Compare & pull request button.
3. Provide a clear title and description for your PR.
4. Submit the pull request for review.

### Testing

- **Write Tests**: Ensure that new features and bug fixes include appropriate tests.
- **Run Tests**: Before submitting a PR, run all tests to ensure they pass.

### Documentation

- **Update README**: If your changes affect the usage or functionality of the project, update the `README.md` accordingly.
- **Inline Documentation**: Add comments and docstrings to explain complex logic and functionalities within the code.

### Style Guides

Adhering to style guides ensures consistency and improves code quality. Follow the guidelines below based on the programming language you are using.

#### Python

- **PEP 8**: Follow the [PEP 8](https://pep8.org/) style guide for Python code.
- **Docstrings**: Use docstrings to document modules, classes, and functions.

    ```python
    def calculate_risk(data):
        """
        Calculate Alzheimer's risk based on genetic data.
        
        Parameters:
            data (dict): Genetic data input.
        
        Returns:
            float: Predicted risk percentage.
        """
        pass
    ```

#### JavaScript

- **ESLint**: Use [ESLint](https://eslint.org/) to maintain consistent coding standards.
- **Prettier**: Integrate [Prettier](https://prettier.io/) for automatic code formatting.

    ```javascript
    // Example of a well-documented function
    /**
     * Calculates the feature importance using SHAP values.
     *
     * @param {Object} data - The input data.
     * @returns {Object} - The feature importance scores.
     */
    function calculateFeatureImportance(data) {
        // Function implementation
    }
    ```

### Acknowledgments

- **Inspiration**: Think of good inspirations

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact Author

For any questions, suggestions, or feedback, please contact the author:

- **Name**: Sam Boesen
- **Email**: sam.boesen2@gmail.com
- **GitHub**: [sboesen2](https://github.com/sboesen2)

