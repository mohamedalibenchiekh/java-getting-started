pipeline {
    agent any

    tools {
        // Specify the JDK installation defined in Jenkins Global Tools Configuration
        jdk 'jdk-21'
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
            // Optionally, clean up the Maven build directory
            sh 'rm -rf target'
        }
    }
}
