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
                    cp target/*.war /opt/tomcat/webapps/petclinic.war
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
