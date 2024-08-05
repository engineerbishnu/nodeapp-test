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

#        stage('Deploy') {
#            steps {
#                script {
#                    // Start npm in the background and get its PID
#                    sh '''
#                    npm start &
#                    NPM_PID=$!
#                    sleep 15
#                    kill $NPM_PID
#                    '''
#                }
#            }
#        }
#
#       // Add further stages as needed
#        // stage('NextStage') {
#        //     steps {
#        //         // Add further steps here
#        //     }
#        // }
#    }

        stage('Deploy') {
            steps {
                script {
                    // Start the Node.js app in the background
                    sh '''
                    nohup npm start > app.log 2>&1 &
                    echo $! > nodeapp.pid
                    '''
                    // Optionally, print the PID of the Node.js process
                    sh 'cat nodeapp.pid'
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
