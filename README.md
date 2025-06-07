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

## 🧠 What I Practiced Today
Freestyle Job

Declarative Pipeline

Multibranch Pipeline

Using sh steps in Jenkinsfile

WAR deployment to Tomcat via Jenkins
