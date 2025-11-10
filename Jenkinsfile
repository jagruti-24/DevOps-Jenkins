pipeline {
    agent any

    tools {
        maven 'Maven-3.9'   // Must match your Maven installation name in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                echo '📥 Cloning repository from GitHub...'
                git branch: 'main', url: 'https://github.com/jagruti-24/DevOps-Jenkins.git'
            }
        }

        stage('Compile') {
            steps {
                echo '🧩 Compiling the source code...'
                sh 'mvn clean compile'
            }
        }

        stage('Build') {
            steps {
                echo '🏗️  Building the project...'
                sh 'mvn package'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running unit tests...'
                sh 'mvn test'
            }
        }

        stage('Post-Build') {
            steps {
                echo '📦 Archiving build artifacts...'
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
