pipeline {
    agent any

    tools {
        maven 'maven3'   // Must match Maven tool name in Jenkins
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/vanshrastogi111/Petclinic.git', branch: 'main'
            }
        }pipeline {
    agent any

    tools {
        maven 'maven3'   // Must match Maven tool name in Jenkins
    }
    environment{
        SCANNER_HOME=tool 'sonar-scanner'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/vanshrastogi111/Petclinic.git', branch: 'main'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Sonarqube analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                     sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Petclinic \
                    -Dsonar.java.binaries=. \
                    -Dsonar.projectKey=Petclinic '''
    
}
            }
        }


        stage('Deploy to Tomcat') {
            steps {
                sh '''
                    echo "📦 Copying WAR file to Tomcat webapps..."
                    cp target/*.war /opt/apache-tomcat-9.0.65/webapps
                '''
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sh '''
                    echo "📦 Copying WAR file to Tomcat webapps..."
                    cp target/*.war /opt/apache-tomcat-9.0.65/webapps
                '''
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
