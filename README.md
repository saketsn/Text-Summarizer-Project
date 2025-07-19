## End-to-End Text Summarization Project
This project demonstrates the complete pipeline for building a text summarizer using Natural Language Processing (NLP). It includes configuration-driven modular development, integration of multiple stages (data ingestion to model evaluation), and deployment readiness with CI/CD.

# Workflow Overview
Configure config.yaml

Set hyperparameters in params.yaml

Define project entities

Manage configurations in the src/config module

Implement components (data transformation, model training, etc.)

Assemble pipeline stages

Develop and test main.py for orchestrating the pipeline

Build and launch the app using app.py

# How to Run the Project Locally
Step 1: Clone the Repository
git clone https://github.com/saketsn/Text-Summarizer-Project.git
cd Text-Summarizer-Project

Step 2: Create and Activate a Virtual Environment (Conda)
conda create -n summary python=3.8 -y
conda activate summary

Step 3: Install Dependencies
pip install -r requirements.txt

Step 4: Run the Application
python app.py



# Deployment: AWS CI/CD with GitHub Actions
Step 1: AWS Setup
Log in to the AWS Console

Create a new IAM user with:

AmazonEC2FullAccess

AmazonEC2ContainerRegistryFullAccess

Step 2: Create AWS Resources
ECR (Elastic Container Registry): Create a new repository to store your Docker image.

Example URI: your-aws-account-id.dkr.ecr.region.amazonaws.com/text-summarizer

EC2 (Elastic Compute Cloud): Launch a new Ubuntu instance.

Step 3: Install Docker on EC2
sudo apt-get update -y
sudo apt-get upgrade -y
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker


Step 4: Configure EC2 as a GitHub Self-Hosted Runner
Go to your GitHub Repository
→ Settings → Actions → Runners → New self-hosted runner

Select your operating system

Follow the given shell commands to register your EC2 instance as a runner

Step 5: Set Up GitHub Secrets
In your GitHub repository → Settings → Secrets and variables → Actions, add the following secrets:

Name	Description
AWS_ACCESS_KEY_ID	IAM user's access key
AWS_SECRET_ACCESS_KEY	IAM user's secret access key
AWS_REGION	        AWS region (e.g., us-east-1)
AWS_ECR_LOGIN_URI	Your ECR login URI
ECR_REPOSITORY_NAME	Name of your ECR repo

# CI/CD Pipeline Summary
Build Docker image of the project code

Push the Docker image to AWS ECR

Launch EC2 instance and pull image from ECR

Run Docker container in EC2 using GitHub Actions


# Project Structure
TEXT-SUMMARIZATION-NLP-PROJECT/
├── .github/
│   └── ... (GitHub Actions/workflow files)
├── config/
│   └── config.yaml                      # Main configuration file
├── research/                            # Jupyter notebooks for experiments
│   ├── 01_data_ingestion.ipynb
│   ├── 02_data_validation.ipynb
│   ├── 03_data_transformation.ipynb
│   ├── 04_model_trainer.ipynb
│   ├── 05_model_evaluation.ipynb
│   ├── Text_Summarization.ipynb
│   └── trials.ipynb
├── src/
│   └── textSummarizer/
│       ├── config/
│       │   ├── __init__.py
│       │   └── configuration.py         # Configuration handling logic
│       ├── components/
│       │   ├── __init__.py
│       │   ├── data_ingestion.py
│       │   ├── data_transformation.py
│       │   ├── data_validation.py
│       │   ├── model_evaluation.py
│       │   └── model_trainer.py
│       ├── constants/
│       │   └── __init__.py              # Constant values used across the project
│       ├── entity/
│       │   └── __init__.py              # Data class definitions
│       ├── logging/
│       │   └── __init__.py              # Custom logging setup
│       ├── pipeline/
│       │   ├── __init__.py
│       │   ├── prediction.py
│       │   ├── stage_01_data_ingestion.py
│       │   ├── stage_02_data_validation.py
│       │   ├── stage_03_data_transformation.py
│       │   ├── stage_04_model_trainer.py
│       │   └── stage_05_model_evaluation.py
│       └── utils/
│           ├── __init__.py
│           └── common.py                # Helper functions
├── app.py                               # Entry point for the web app
├── Dockerfile                           # Docker setup file
├── LICENSE
├── main.py                              # Main pipeline runner
├── params.yaml                          # Hyperparameters configuration
├── README.md
├── requirements.txt                     # Python dependencies
├── setup.py                             # Package installation configuration
├── template.py                          # CLI/Template generation
└── test.py                              # Test script

<img width="308" height="469" alt="image" src="https://github.com/user-attachments/assets/117dadb6-2e49-459c-920e-602e0639979e" />
<img width="387" height="348" alt="image" src="https://github.com/user-attachments/assets/df71a5bd-2515-4ef2-b0f7-7e977e038417" />
<img width="377" height="850" alt="image" src="https://github.com/user-attachments/assets/f7a02b1d-77bd-4940-b73f-90bb8a15cee7" />






