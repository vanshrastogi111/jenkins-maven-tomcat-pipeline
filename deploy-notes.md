# 📘 Jenkins Deployment Notes

## ✔️ Jenkins Configuration

- Maven Tool: `maven3`
- JDK: `jdk11` (optional)
- Project repo: `https://github.com/vanshrastogi111/Petclinic.git`
- Branch: `main`

## 🧩 Jenkins Job Types Practiced

- Freestyle Job
- Pipeline Job (with Jenkinsfile)
- Multibranch Pipeline (auto-branch detection)

## 🐱 Tomcat

- Installed in `/opt/tomcat`
- WAR copied to `webapps/` directory

## 📦 Maven

- Used `mvn clean package` to build WAR
- Output: `target/*.war` → deployed to Tomcat

## 🔗 Sample App Access

```bash
http://localhost:8080/petclinic
