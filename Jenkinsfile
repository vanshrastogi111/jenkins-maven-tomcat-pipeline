pipeline {
    agent any

    tools {
        maven 'maven3'
    }

    environment {
        SCANNER_HOME = tool 'sonar-scanner'
    }

    stages {

        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/vanshrastogi111/Petclinic.git'
            }
        }

        stage('Compile') {
            steps {
                sh "mvn clean compile"
            }
        }

        stage('Test cases') {
            steps {
                sh "mvn test"
            }
        }

        stage('Sonarqube analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner \
                        -Dsonar.projectName=Petclinic \
                        -Dsonar.java.binaries=. \
                        -Dsonar.projectKey=Petclinic'''
                }
            }
        }

        stage('Build') {
            steps {
                sh "mvn clean package"
            }
        }

        stage('OWASP Dependency Check') {
            options {
                retry(2)
            }
            steps {
                script {
                    dependencyCheck additionalArguments: '--scan target/', odcInstallation: 'owasp'
                }
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

        stage('Deploy to Nexus') {
            steps {
                configFileProvider([configFile(fileId: '706d7a68-e282-4117-bebf-36b122d045c4', variable: 'mavensettings')]) {
                    sh "mvn -s $mavensettings clean deploy -DskipTests=true"
                }
            }
        }

        stage('Tomcat Deploy') {
            steps {
                sh "sudo cp target/petclinic.war /opt/apache-tomcat-9.0.65/webapps"
            }
        }
    }
}
