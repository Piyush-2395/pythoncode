pipeline {
    agent any
    environment {
        // Set up any environment variables here if needed
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Install dependencies
                    sh '''
                    python3 -m venv venv
                    source venv/bin/activate
                    pip install -r requirements.txt
                    '''
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run tests
                    sh '''
                    source venv/bin/activate
                    pytest
                    '''
                }
            }
        }
        stage('Deploy') {
            when {
                branch 'main' // Adjust the branch name if needed
            }
            steps {
                script {
                    // Deploy to staging or production
                    // Example: Deploy script or commands
                    echo 'Deploying to staging environment...'
                    // Add your deployment commands here
                }
            }
        }
    }
    post {
        always {
            // Cleanup actions or notifications
            echo 'Cleaning up...'
            sh 'deactivate'
        }
        success {
            // Notify on success
            echo 'Build and tests succeeded!'
        }
        failure {
            // Notify on failure
            echo 'Build or tests failed!'
        }
    }
}
