## 🔍 SonarQube Integration

**SonarQube** is an open-source platform for continuous inspection of code quality. It performs **static code analysis** to detect bugs, vulnerabilities, code smells, and duplications, helping developers maintain high-quality, secure, and maintainable code.

---

### ✅ Key Features

- **Static Code Analysis**: Scans your code for bugs, vulnerabilities, and code smells.
- **Code Quality Metrics**: Tracks metrics like test coverage, cyclomatic complexity, and duplications.
- **Issue Tracking**: Categorizes issues by severity and provides detailed context and suggested fixes.
- **CI/CD Integration**: Supports integration with Jenkins, GitHub Actions, GitLab CI, and others.
- **Custom Rules & Profiles**: Configure custom quality gates and rules to enforce coding standards.
- **IDE Integration**: Receive real-time feedback in popular IDEs (e.g., IntelliJ, VSCode).

---

### 🐳 Install SonarQube with Docker

To set up a local SonarQube server:

docker run -d --name sonarqube -p 9000:9000 sonarqube:lts-community

### Access SonarQube at: http://localhost:9000
Default credentials:

Username: admin

Password: admin (you will be prompted to change it on first login)
