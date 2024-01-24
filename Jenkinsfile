pipeline {
    agent any

    environment {
        // Define environment variables if needed
        // Example: MY_VARIABLE = 'value'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from version control
                // Example: git 'https://github.com/your/repository.git'
            }
        }

        stage('Build') {
            steps {
                // Build your project
                // Example: sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run your tests
                // Example: sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                // Deploy your application or artifacts
                // Example: sh 'deploy-script.sh'
            }
        }
    }

    post {
        success {
            // Actions to perform when the pipeline succeeds
            // Example: echo 'Build successful, notify team'
        }
        failure {
            // Actions to perform when the pipeline fails
            // Example: mail to: 'team@example.com', subject: 'Build failed', body: 'Please check Jenkins for details.'
        }
    }
}
