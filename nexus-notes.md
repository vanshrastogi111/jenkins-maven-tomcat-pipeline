# 📦 Nexus Repository Manager - Quick Guide

## 🧠 What is It?

Nexus Repository Manager is a central hub for storing and managing software artifacts like JARs, libraries, and binaries. It supports CI/CD, versioning, and secure distribution.

---

## 🚀 Use Case: DevOps with Microservices

- Store all microservice artifacts centrally
- Proxy/caching for external dependencies (e.g., Maven Central)
- Integrates with CI tools like Jenkins for artifact publishing
- Supports access control and version traceability

---

## 🛠️ Install on Linux

```bash
wget https://download.sonatype.com/nexus/3/latest-unix.tar.gz
tar -xf latest-unix.tar.gz
cd nexus-*/bin
chmod +x nexus
./nexus start
Access UI: http://localhost:8081
```
Or via Docker:
```bash
docker run -d --name nexus -p 8081:8081 sonatype/nexus3
```
🔗 Maven Setup
In pom.xml:

```xml
<distributionManagement>
  <repository>
    <id>maven-releases</id>
    <url>http://<nexus-ip>:8081/repository/maven-releases/</url>
  </repository>
</distributionManagement>
In ~/.m2/settings.xml:
```
```xml
<server>
  <id>maven-releases</id>
  <username>your-username</username>
  <password>your-password</password>
</server>
```
🧪 Deployment
With Maven:

```bash
mvn clean deploy
```
With Jenkins:

```groovy
configFileProvider([configFile(fileId: 'your-file-id', variable: 'mavensettings')]) {
    sh "mvn -s $mavensettings clean deploy -DskipTests=true"
}
```
