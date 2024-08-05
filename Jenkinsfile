pipeline {
    agent any

    environment {
        // Set environment variables if needed
        NODE_ENV = 'development'
        PORT = '3000' // Make sure this matches the port your Node.js app is using
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
                    // Start the Node.js app in the background
                    sh '''
                    nohup npm start > app.log 2>&1 &
                    echo $! > nodeapp.pid
                    '''
                    // Optionally print the PID for reference
                    sh 'cat nodeapp.pid'
                }
            }
        }

        stage('Print URL') {
            steps {
                script {
                    // Print the URL where the Node.js app can be accessed
                    def url = "http://${env.NODEJS_HOST}:${env.PORT}"
                    echo "Your Node.js application is running at: ${url}"
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
