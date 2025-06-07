# 🔧 Jenkins + Maven + Tomcat CI/CD Pipeline

This project demonstrates a simple CI/CD pipeline using Jenkins, Maven, and Apache Tomcat. The pipeline is built using Jenkins Declarative syntax and is designed to:

- Clone a Java project from GitHub
- Build it using Maven
- Deploy the generated `.war` file to a local Tomcat server

---

## 🛠 Tools Used

- **Jenkins**
- **Apache Maven**
- **Apache Tomcat**
- **GitHub**
- **Linux (Ubuntu)**

---



## 🚀 Pipeline Stages

1. **Clone** the Petclinic repository
2. **Build** using `mvn clean package`
3. **Deploy** the `.war` to `/opt/tomcat/webapps/`

---

## 🌐 Access the App

After deployment: http://your-ip:8080/petclinic

## 📌 Notes
Maven and JDK must be configured in Jenkins under Global Tools.

Jenkins must have write access to the Tomcat webapps folder.


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
