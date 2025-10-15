# CI/CD Pipeline with Jenkins & Python (Pytest Integration)

This project demonstrates a **complete CI/CD workflow using Jenkins**, Python, and Pytest-based automated testing. The repository contains a simple Python application along with unit tests, and a **Jenkinsfile** that defines the pipeline stages for build and test automation.

---

##  Features

- ✅ Python app with basic functions (`add()` & `subtract()`)
- ✅ Unit testing with **Pytest**
- ✅ **Jenkinsfile** configured for:
  - Virtual environment setup
  - Installing dependencies from `requirements.txt`
  - Running automated test cases
- ✅ **Continuous Integration** workflow: GitHub → Jenkins → Build → Test → Result Report

---

## 🧠 Tech Stack & Tools

| Component      | Purpose                              |
|---------------|--------------------------------------|
| **Python**     | Core programming language            |
| **Pytest**     | Test automation framework            |
| **Jenkins**    | CI/CD pipeline automation            |
| **GitHub**     | Source code repository               |
| **Jenkinsfile**| Pipeline as code (Scripted stages)   |
| **Virtualenv** | Python environment isolation         |

---

## ⚙️ Pipeline Workflow (Jenkinsfile Stages)

1. **Setup Python Environment**
2. **Install Dependencies**
3. **Execute Unit Tests using Pytest**
4. **Report Build Status (Success/Failure)**

```groovy
pipeline {
    agent any
    stages {
        stage('Setup Python Env') {
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }
        stage('Run Tests') {
            steps {
                sh '''
                    . venv/bin/activate
                    pytest
                '''
            }
        }
    }
}
