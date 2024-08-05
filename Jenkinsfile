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

        stage('Build') {
            steps {
                script {
                    // Build your application if needed
                    sh 'npm run build'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Start npm in the background and save its PID
                    sh '''
                    nohup npm start > app.log 2>&1 &
                    echo $! > nodeapp.pid
                    '''
                    // Optionally print the PID for reference
                    sh 'cat nodeapp.pid'
                }
            }
        }

        // Add further stages as needed
        stage('NextStage') {
            steps {
                script {
                    // Add further steps here
                    echo 'Proceeding to the next stage...'
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
            echo 'Pipeline finished.'
        }
    }
}
