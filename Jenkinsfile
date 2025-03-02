pipeline {
    agent any

    environment {
        GITHUB_REPO = 'https://github.com/nandinivijay/jenkinspipeline.git'
        BRANCH = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: "${BRANCH}", url: "${GITHUB_REPO}"
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'echo Building project...'
                    // Add actual build commands here, e.g., Maven or Gradle
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh 'echo Running tests...'
                    // Add test commands here, e.g., unit tests
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'echo Deploying application...'
                    // Add deployment commands here, e.g., Docker push, SCP to server, etc.
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
