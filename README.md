# Azure DevOps + Azure Databricks CI/CD Integration 🚀  
> Seamless Continuous Integration and Deployment with Azure DevOps & Databricks  

![Pipeline Architecture](https://drive.google.com/uc?export=view&id=1r0IupR-qtZYp8mJZGLnkeZeVYrB-7-qO)  
![Execution Flow](https://drive.google.com/uc?export=view&id=1VTZSN4Bzl6OgraJah8RuKZdkk5EgvKpL)

## 📌 Project Overview
This project showcases the implementation of a robust CI/CD pipeline using **Azure DevOps** integrated with **Azure Databricks**. The pipeline is designed to automate version control, testing, deployment, and synchronization of Databricks notebooks and jobs via Azure Repos and Azure Pipelines.

## 💡 Objective
To automate the development lifecycle of data engineering and machine learning notebooks in Databricks, enabling:
- Faster delivery cycles
- Better collaboration via version control
- Secure, seamless deployments through CI/CD
- Minimal manual effort and error-prone steps

---

## 🛠️ Tools & Technologies
- **Azure DevOps**: For version control (Azure Repos), build, and release pipelines
- **Azure Databricks**: For scalable data processing, notebooks, and job execution
- **Databricks CLI & REST APIs**: For automation and remote deployment
- **Azure Key Vault**: For secret and credential management
- **Git**: For local version control and syncing with Azure Repos

---

## 🧱 What is Azure DevOps?
Azure DevOps is a suite of development tools that supports the complete software development lifecycle:
- **Azure Repos**: Source control using Git
- **Azure Pipelines**: Build and deploy automation
- **Azure Boards, Test Plans, Artifacts**: (not used here, but part of the suite)

---

## 🧠 What is Azure Databricks?
Azure Databricks is a unified data analytics platform that supports big data processing, real-time analytics, and machine learning using Apache Spark.

It allows data engineers and scientists to develop and run scalable pipelines, notebooks, and machine learning workflows.

---

## 🔁 CI/CD Architecture: High-Level Flow

1. **Notebook files and configurations** are stored in Azure Repos.
2. **Build Pipeline**: Triggers on every commit to validate code and upload it to a staging folder.
3. **Release Pipeline**: Deploys notebooks and job configs into Azure Databricks using Databricks CLI or REST APIs.
4. Changes in notebooks can also be synced **back into Azure Repos** using Databricks Repos integration or CLI export commands.

---

## 🔒 Security and Key Management

Security was a major priority in this project:
- **Azure Key Vault** stored all sensitive credentials, tokens, and client secrets.
- **Service Principal** was created with RBAC permissions for Databricks workspace access.
- **Pipelines** accessed secrets from Key Vault securely using managed identities and linked service connections.
- Access was granted using **least-privilege principles** for both DevOps and Databricks users.

---

## ⚙️ Steps to Set Up

### 1. Set Up Azure DevOps Repo & Pipelines
- Created a new repo and committed initial notebook files (`.dbc`, `.py` or `.ipynb`)
- Added `azure-pipelines.yml` for build pipeline
- Configured release stages with tasks for Databricks CLI or REST calls

### 2. Connect Azure DevOps to Databricks
- Registered an **Azure Service Principal**
- Generated **Personal Access Token (PAT)** in Databricks
- Created **Service Connections** in Azure DevOps using Key Vault-stored secrets

### 3. Automate Deployment
- Any commit in `main` triggers notebook upload
- Build pipeline checks syntax, format, and metadata
- Release pipeline syncs changes into Databricks workspace or job folders

---

## ⚠️ Challenges Faced

- **Databricks CLI Authentication**: Setting up secure auth using tokens and service principals.
- **Environment Sync**: Ensuring notebooks stayed in sync when edited from both Databricks and DevOps.
- **Secrets Management**: Avoiding hardcoded tokens, managing secure pipeline access.
- **Pipeline Debugging**: Handling API rate limits, transient errors, and failed deployment logs.

---

## 📁 Folder Structure

