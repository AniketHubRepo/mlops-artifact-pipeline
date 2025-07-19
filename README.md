# MLOps Artifact Pipeline  

## Project Overview  
This project demonstrates a complete MLOps pipeline using GitHub Actions for a simple digit classification task. We’ve used a Logistic Regression model trained on the `digits` dataset from `sklearn`, and automated the entire ML lifecycle — training, testing, and inference — using CI/CD.  

## Objectives  
- Train a Logistic Regression model on the `digits` dataset.  
- Load hyperparameters from a JSON config file.  
- Save the trained model as a `.pkl` file (artifact).  
- Write unit tests for the training and config setup.  
- Set up three GitHub Actions workflows:  
  - Model Training  
  - Testing using Pytest  
  - Inference with job dependencies  
- Pass model artifacts between jobs using `upload-artifact` and `download-artifact`  

## Directory Structure  
.  
├── .github/  
│ └── workflows/  
│ ├── train.yml  
│ ├── test.yml  
│ └── inference.yml  
├── config/  
│ └── config.json  
├── src/  
│ ├── train.py  
│ └── inference.py  
├── tests/  
│ └── test_train.py  
├── .gitignore  
├── model_train.pkl  
├── README.md  
└── requirements.txt  

## Setup Instructions

1. Create and activate a conda environment:  
   conda create -n mlops2 python=3.10 -y  
   conda activate mlops2  
  
2. Install the required packages:  
pip install -r requirements.txt  
  
3. Run model training:  
python src/train.py  
Run unit tests:  
pytest tests/test_train.py  
  
4. Run inference:  
python src/inference.py  
  
  
## GitHub Actions Workflows  
train.yml: Trains the model and saves model_train.pkl as an artifact.  
test.yml: Executes unit tests using Pytest.  
inference.yml: Runs jobs in sequence (test → train → inference) with artifact sharing.  
  
## Branching Strategy  
We used a clean, incremental branching strategy:  
  
main: Initial setup and README  
  
classification_branch: Added training logic  
  
test_branch: Added testing logic  
  
inference_branch: Added inference and full pipeline  
  
Each branch builds logically over the previous for traceability.  
  
## Output Artifact  
The trained model is saved as model_train.pkl and passed across jobs using:  
actions/upload-artifact  
actions/download-artifact  
  
## Details  
Name: Aniket Srivastava  
Roll No: G24AI1077  
Repository link: https://github.com/AniketHubRepo/mlops-artifact-pipeline.git  
