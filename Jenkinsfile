pipeline {
    agent any // Use any available agent
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'


                // Command to install dependencies
                // sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Command to run your tests
                // sh 'npm test'
            }
        }
          stage('Deploy to EC2') {
            steps {
                script {
                    // SSH command to navigate to the backend folder, pull the latest code, and restart PM2
                    def sshCommand = """
                        ssh ${REMOTE_HOST_QA_NAME}@${REMOTE_HOST_QA} << 'EOF'
                        echo "Connecting to EC2 instance..."                       
                        EOF
                    """
                    echo 'Deploying to EC2...'
                    sh sshCommand
                }
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
