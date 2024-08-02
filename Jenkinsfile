pipeline {
    agent any

    environment {
        // Set environment variables if needed
        NODE_ENV = 'development'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your repository
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install Node.js dependencies
                    sh 'npm install'
                }
            }
        }



        stage('Deploy') {
            steps {
                script {
                    // Deploy your application (example, replace with actual deployment commands)
                    // e.g., copying build artifacts to a server, deploying to cloud, etc.
                    sh 'echo "Deploying application"'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed.'
        }
        always {
            // Clean up or notify
            echo 'Pipeline finished.'
        }
    }
}
