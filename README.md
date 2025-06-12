# 🐾 Petclinic CI/CD Pipeline with Jenkins

This project uses a Jenkins Declarative Pipeline to automate the build, test, analysis, security scan, deployment, and artifact publication process for the **Spring Petclinic** application.

---

## 🚀 Pipeline Overview

### 🔧 Tools & Environment

- **Maven** (`maven3`)
- **SonarQube Scanner** (`sonar-scanner`)
- **OWASP Dependency Check**
- **Nexus Repository**
- **Apache Tomcat**

---

## 🔄 Jenkins Pipeline Stages

### 1. **Git Checkout**
- Clones the `main` branch from the GitHub repository:
https://github.com/vanshrastogi111/Petclinic.git

### 2. **Compile**
- Compiles the source code using:
```bash
mvn clean compile
```

### 3. Test Cases
Runs all unit tests:

```bash
mvn test
```
### 4. SonarQube Analysis
Performs static code analysis with SonarQube:

```bash
sonar-scanner \
  -Dsonar.projectName=Petclinic \
  -Dsonar.java.binaries=. \
  -Dsonar.projectKey=Petclinic
```
### 5. Build
Packages the application into a WAR file:

```bash
mvn clean package
```
### 6. OWASP Dependency Check
Scans for known security vulnerabilities in dependencies.

### 7. Publish OWASP Report
Publishes the dependency-check-report.html to the Jenkins job UI.

### 8. Deploy to Nexus
Publishes artifacts to a Nexus Repository using a Maven settings file.

### 9. Tomcat Deployment
Deploys the WAR file to a local Apache Tomcat server:

```bash
sudo cp target/petclinic.war /opt/apache-tomcat-9.0.65/webapps
```

## 🧪 Prerequisites- 
### Notes and quick guide for each is present in the repository
Jenkins with required plugins:

Maven Integration

SonarQube Scanner

OWASP Dependency-Check

Config File Provider

SonarQube server configured in Jenkins (sonar-server)

Nexus repository and credentials configured

Apache Tomcat installed locally

### 📌 Notes
Ensure your Jenkins agent has permission to deploy to Tomcat (sudo rights).

Replace placeholders like sonar-server, mavensettings, and Nexus file IDs with your own configuration IDs in Jenkins.

Customize SonarQube and Nexus details according to your environment.


## **Jenkins Job Tutorial**

In this tutorial, we'll walk you through the process of creating three types of Jenkins jobs: Freestyle, Pipeline, and Multibranch. Each job will have stages for Git checkout, Maven compile, Maven package, and deploying to Tomcat. Let's get started!

### **Freestyle Job**

1. From the Jenkins dashboard, click on "New Item" to create a new job.
2. Enter a name for the job and select "Freestyle project" as the job type.
3. In the job configuration page, go to the "Source Code Management" section and choose your Git repository. Configure the branch or repository URL as per your requirements.
4. In the "Build" section, click on "Add build step" and select "Execute shell" from the dropdown.
5. In the shell script section, enter the following commands:

```shell
#!/bin/bash

# Git checkout
git checkout <branch_name>

# Maven compile
mvn compile

# Maven package
mvn package

# Deploy to Tomcat
# Replace 'webapp.war' with your generated WAR file name and adjust the Tomcat server details
cp target/webapp.war /path/to/tomcat/webapps/
```

6. Click on "Save" to save the job configuration.

### **Pipeline Job**

1. From the Jenkins dashboard, click on "New Item" to create a new job.
2. Enter a name for the job and select "Pipeline" as the job type.
3. In the job configuration page, scroll down to the "Pipeline" section.
4. Choose the "Pipeline script" option and enter the Jenkinsfile:
5. Click on "Save" to save the job configuration.

### **Multibranch Job**

1. From the Jenkins dashboard, click on "New Item" to create a new job.
2. Enter a name for the job and select "Multibranch Pipeline" as the job type.
3. In the job configuration page, go to the "Branch Sources" section.
4. Configure the source for your Git repository, such as GitHub or Bitbucket, and provide the necessary credentials and repository details.
5. In the "Build Configuration" section, click on "Add build step" and select "Pipeline script" from the dropdown.
6. Enter the same pipeline script mentioned in the Pipeline Job section.
7. Click on "Save" to save the job configuration.
