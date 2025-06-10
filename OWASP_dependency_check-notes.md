# 🛡️ OWASP Dependency Check Integration

This project uses [OWASP Dependency Check](https://owasp.org/www-project-dependency-check/) — a Software Composition Analysis (SCA) tool — to identify known vulnerabilities in third-party dependencies.

---

## 🔍 What is OWASP Dependency Check?

OWASP Dependency Check is a tool that:

- Scans your project’s dependencies
- Detects known security vulnerabilities (CVEs)
- Provides detailed HTML reports
- Supports Maven, Gradle, Jenkins, and standalone usage

---

## 🚀 Jenkins Integration Steps

### ✅ Plugin Installation

1. Go to **Manage Jenkins** → **Manage Plugins**
2. Search for `OWASP Dependency-Check Plugin`
3. Install it (no restart needed)
4. Go to **Manage Jenkins** → **Global Tool Configuration**
5. Add a new **OWASP Dependency Check** installation (e.g., name it `owasp`)

### 🛠️ Pipeline Example

```groovy
stage('OWASP Dependency Check') {
    steps {
        dependencyCheck additionalArguments: '--scan target/', odcInstallation: 'owasp'
    }
}

stage('Publish OWASP Dependency Check Report') {
    steps {
        publishHTML(target: [
            allowMissing: false,
            alwaysLinkToLastBuild: true,
            keepAll: true,
            reportDir: 'target',
            reportFiles: 'dependency-check-report.html',
            reportName: 'OWASP Dependency Check Report'
        ])
    }
}
```

## 🧪 Standalone JAR Usage
Download the latest dependency-check.jar from Releases

Run the following:

```bash
java -jar dependency-check.jar --project <project-name> --scan <path-to-project>
```
## 📦 Maven Integration
Add the following to your pom.xml:
```
xml
Copy
Edit
<plugin>
  <groupId>org.owasp</groupId>
  <artifactId>dependency-check-maven</artifactId>
  <version>INSERT_VERSION_HERE</version>
  <executions>
    <execution>
      <goals>
        <goal>check</goal>
      </goals>
    </execution>
  </executions>
</plugin>
Run with:
```
```
mvn dependency-check:check
```
## 📊 Report Location
Method	Path
Standalone	target/dependency-check-report.html
Maven	target/dependency-check-report.html
Gradle	build/reports/dependency-check-report.html

Open the HTML file in your browser to view the results.

## Resources

- [OWASP Dependency Check GitHub Repository](https://github.com/jeremylong/DependencyCheck)
- [OWASP Dependency Check Official Website](https://owasp.org/www-project-dependency-check/)
