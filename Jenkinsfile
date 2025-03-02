pipeline {
    agent any

    options {
        timeout(time: 30, unit: 'MINUTES') // Set a timeout for the pipeline
       
        retry(3)
    }

    parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: 'Branch to build')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run tests')
        choice(name: 'DEPLOY_ENV', choices: ['dev', 'staging', 'production'], description: 'Deployment environment')
    }

    environment {
        GITHUB_REPO = 'https://github.com/nandinivijay/jenkinspipeline.git'
        BRANCH = params.BRANCH
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
            when {
                expression { params.RUN_TESTS }
            }
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
                    sh "echo Deploying application to ${params.DEPLOY_ENV}..."
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
