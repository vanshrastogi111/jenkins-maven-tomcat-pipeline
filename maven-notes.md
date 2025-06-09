## ☕ Maven Notes for CI/CD Pipeline

**Maven** is a powerful build automation tool primarily used for Java projects. It plays a central role in our CI/CD pipeline to manage dependencies, automate builds, and support testing and deployment.



### 🧩 Key Maven Roles in CI/CD

1. **Project Setup**
   - Maven standardizes the project structure using archetypes.
   - `pom.xml` is used to define metadata, dependencies, and plugin configurations.

2. **Dependency Management**
   - External libraries are declared in `pom.xml`.
   - Maven resolves dependencies from remote repositories (e.g., Maven Central).

3. **Build Automation**
   - Source code compilation
   - Test execution
   - Packaging (e.g., JAR, WAR)
   - Artifact installation or deployment

4. **Testing & Quality**
   - Integrates with frameworks like JUnit for automated testing.
   - Can be extended with plugins for static analysis (e.g., SonarQube).

5. **Continuous Integration**
   - Maven commands are triggered in CI pipelines on each commit or PR.
   - Ensures repeatable, consistent builds across environments.

6. **Deployment**
   - Maven can generate deployable artifacts (WAR/JAR).
   - CI/CD tools can push these artifacts to servers or cloud platforms.

7. **Updates**
   - Maven simplifies dependency upgrades and version conflict resolution.

---

### 🔁 Maven Build Lifecycle

Maven operates via three main lifecycles:

#### 1. Clean Lifecycle
- `mvn clean`: Deletes previous build artifacts.

#### 2. Default Lifecycle
- `mvn validate`: Validates project structure.
- `mvn compile`: Compiles source code.
- `mvn test`: Runs unit tests.
- `mvn package`: Packages code (e.g., `.jar` or `.war`).
- `mvn install`: Installs artifact to local repo (`~/.m2`).
- `mvn deploy`: Deploys artifact to remote repo (e.g., Nexus).

#### 3. Site Lifecycle
- `mvn site`: Generates documentation.
- `mvn site-deploy`: Publishes documentation to a web server.

---

### 🧪 Common Maven Commands in CI/CD

| Command           | Description                                  |
|------------------|----------------------------------------------|
| `mvn compile`     | Compiles the source code                     |
| `mvn test`        | Executes unit tests                          |
| `mvn package`     | Builds project into a distributable format   |
| `mvn install`     | Installs artifact to local Maven repository  |
| `mvn deploy`      | Uploads artifact to a remote repository      |
| `mvn clean`       | Cleans previous build outputs                |
| `mvn site`        | Generates project documentation              |

---


Maven ensures builds are **reproducible**, **portable**, and **consistent**, making it a vital tool in modern DevOps and CI/CD workflows.
