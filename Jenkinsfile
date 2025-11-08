pipeline {
    agent any

    tools {
        // Use the JDK name configured in Jenkins Global Tools Configuration
        jdk 'Java17'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/mohamedalibenchiekh/java-getting-started.git'
            }
        }
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        stage('Test') {
            steps {
                sh './mvnw test'
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            sh 'rm -rf target'
        }
    }
}
