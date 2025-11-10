pipeline {
    agent any

    tools {
        maven 'Maven_3_9_9'
        jdk 'jdk17'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository from GitHub...'
                git branch: 'main', url: 'https://github.com/jagruti-24/DevOps-Jenkins.git'
            }
        }

        stage('Compile') {
            steps {
                echo 'Compiling source code...'
                sh 'mvn clean compile'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh 'mvn test'
            }
        }

        stage('Post-Build') {
            steps {
                echo 'Archiving build artifacts...'
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Build completed successfully!'
        }
        failure {
            echo '❌ Build failed. Please check console logs.'
        }
    }
}
