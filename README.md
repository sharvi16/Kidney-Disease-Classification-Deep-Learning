# Kidney Disease Classification Deep Learning Project

## Workflows

1. Update `config.yaml`
2. Update `secrets.yaml` [Optional]
3. Update `params.yaml`
4. Update the entity
5. Update the configuration manager in `src/config`
6. Update the components
7. Update the pipeline
8. Update `main.py`
9. Update `dvc.yaml`
10. Update `app.py`

## How to run?

### STEPS:

**Clone the repository**

```bash
git clone https://github.com/sharvi16/Kidney-Disease-Classification-Deep-Learning
```

**STEP 01- Create a conda environment after opening the repository**

```bash
conda create -n cnncls python=3.8 -y
conda activate cnncls
```

**STEP 02- Install the requirements**

```bash
pip install -r requirements.txt
```

**Finally run the following command**

```bash
python app.py
```

Now, open up your local host and port.

---

## MLflow

### Documentation
[MLflow tutorial](https://mlflow.org/docs/latest/index.html)

### Local UI
```bash
mlflow ui
```

### DagsHub Integration

```bash
export MLFLOW_TRACKING_URI=https://dagshub.com/entbappy/Kidney-Disease-Classification-MLflow-DVC.mlflow
export MLFLOW_TRACKING_USERNAME=entbappy 
export MLFLOW_TRACKING_PASSWORD=6824692c47a369aa6f9eac5b10041d5c8edbcef0
```

Run your script:
```bash
python script.py
```

---

## DVC Commands

```bash
dvc init
dvc repro
dvc dag
```

---

## About MLflow & DVC

### MLflow
- Production Grade
- Trace all of your experiments
- Logging & tagging your model

### DVC
- Lightweight for POC
- Lightweight experiment tracker
- Orchestration (Creating Pipelines)

---

## AWS CICD Deployment with Github Actions

### 1. Login to AWS console.
### 2. Create IAM user for deployment with specific access:
1. **EC2 access**: Virtual machine
2. **ECR**: Elastic Container Registry to save your docker image in AWS

#### Description: About the deployment
1. Build docker image of the source code
2. Push your docker image to ECR
3. Launch Your EC2 
4. Pull Your image from ECR in EC2
5. Launch your docker image in EC2

#### Policy:
1. `AmazonEC2ContainerRegistryFullAccess`
2. `AmazonEC2FullAccess`

### 3. Create ECR repo to store/save docker image
- Save the URI: `566373416292.dkr.ecr.us-east-1.amazonaws.com/chicken`

### 4. Create EC2 machine (Ubuntu)

### 5. Open EC2 and Install docker in EC2 Machine:

```bash
# optional
sudo apt-get update -y
sudo apt-get upgrade

# required
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```

### 6. Configure EC2 as self-hosted runner:
Settings > Actions > Runner > New self-hosted runner > Choose OS > Run commands one by one

### 7. Setup GitHub secrets:
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_REGION` = `us-east-1`
- `AWS_ECR_LOGIN_URI` = `566373416292.dkr.ecr.ap-south-1.amazonaws.com`
- `ECR_REPOSITORY_NAME` = `simple-app`
