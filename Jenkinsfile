pipeline {
    agent any

    tools {
        maven 'maven-3.9.9'
    }

    environment {
        JAVA_HOME = tool 'jdk-21'
        PATH = "${JAVA_HOME}/bin:${PATH}"
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn -B clean install -DskipTests'
            }
        }

        stage('Docker Compose') {
            steps {
                script {
                    sh 'docker compose -f docker-compose.jenkins.yaml up --build -d'
                }
            }
        }
    }
}