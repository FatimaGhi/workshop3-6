pipeline {
    agent any

    tools {
        maven 'apache_maven'
        jdk 'Java_17'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/FatimaGhi/workshop3-6.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('SCA - OWASP Dependency Check') {
            steps {
                bat 'mvn org.owasp:dependency-check-maven:check'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'target/dependency-check-report.html'
        }
    }
}
