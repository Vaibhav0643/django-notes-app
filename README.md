
---

# 🚀 Jenkins CI/CD Pipeline — Build & Deploy with Docker

## 📘 Overview

This project demonstrates a **Jenkins pipeline** that automates the **build, test, and deployment** process of an application using **Docker**.
The pipeline is triggered automatically on each **code commit**, ensuring consistent and repeatable deployments.

---

## 🧰 Tools & Technologies

* **Jenkins** – Continuous Integration & Continuous Deployment (CI/CD) tool
* **Docker** – Containerization platform for building and running the application
* **GitHub/Git** – Version control system for managing code and pipeline triggers

---

## ⚙️ Pipeline Workflow

### 🔁 Trigger

* The pipeline is automatically triggered on every **commit or pull request** to the main branch.
* Webhook integration is configured between **GitHub** and **Jenkins** to detect code changes.

### 🧱 Stages in `Jenkinsfile`

#### **1. Checkout**

* Jenkins pulls the latest source code from the repository.

#### **2. Build**

* The Docker image for the application is built using the `Dockerfile`.

  ```groovy
  stage('Build') {
      steps {
          sh 'docker build -t myapp:latest .'
      }
  }
  ```

#### **3. Test**

* Optionally, unit or integration tests can be executed inside the container.

  ```groovy
  stage('Test') {
      steps {
          sh 'docker run --rm myapp:latest npm test'  // example for Node.js app
      }
  }
  ```

#### **4. Deploy**

* The container is deployed (locally or to a test server).

  ```groovy
  stage('Deploy') {
      steps {
          sh 'docker run -d -p 8080:8080 myapp:latest'
      }
  }
  ```

---

## 🧩 Jenkins Setup

1. **Install Jenkins**

   * Installed locally / or used a cloud-based Jenkins instance.
   * Installed required plugins:

     * *Git Plugin*
     * *Pipeline Plugin*
     * *Docker Plugin*

2. **Connect Git Repository**

   * Added repository URL in Jenkins job configuration.
   * Enabled “Build when a change is pushed to GitHub” trigger.

3. **Add Jenkinsfile**

   * The `Jenkinsfile` is stored in the root of the project repository.

4. **Configure Docker**

   * Installed Docker on the Jenkins server.
   * Provided Docker access to the Jenkins user:

     ```bash
     sudo usermod -aG docker jenkins
     ```

---

## 🧪 Testing the Pipeline

* Pushed a small code change to trigger the pipeline.
* Jenkins automatically executed all stages:

  * Code checkout ✅
  * Docker build ✅
  * Test (if applicable) ✅
  * Deployment ✅
* Verified successful execution via the Jenkins dashboard.

---

## 📸 Screenshots

Below are screenshots of the successful pipeline run:

1. ✅ **Build and Test Stages Completed**
2. 🚀 **Deployment Stage Successful**
3. 📊 **Pipeline View (All Green Stages)**

*(Screenshots are included in the `screenshots/` folder.)*

---

## 🧾 Summary

This project demonstrates a **fully automated CI/CD workflow** integrating:

* Source Code → Jenkins → Docker → Deployment
  It ensures reliable builds, consistent environments, and faster release cycles.

---

## 💡 Future Enhancements

* Push built Docker images to **Docker Hub or AWS ECR**
* Add automated testing using **JUnit or pytest**
* Implement deployment to **AWS EC2 or Kubernetes**

---

Would you like me to tailor it for a **specific app type** (e.g., Node.js, Python Flask, Java Spring Boot)?
I can adjust the build/test commands and deployment section accordingly to make it look more realistic for your case.
