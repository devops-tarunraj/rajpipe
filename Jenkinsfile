pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git
            }
        }

        stage('Build') {
            steps {
                // Set up Maven
                withMaven(
                    maven: MAVEN_TOOL,
                    mavenSettingsConfig: 'your-maven-settings-id',
                    mavenLocalRepo: '.repository') {
                    // Build the Maven project
                    sh "mvn clean install"
                }
            }
        }

        stage('Deploy to Nexus') {
            steps {
                script {
                    // Deploy artifacts to Nexus
                    withCredentials([usernamePassword(credentialsId: NEXUS_CREDENTIAL_ID, usernameVariable: 'NEXUS_USERNAME', passwordVariable: 'NEXUS_PASSWORD')]) {
                        def mvnHome = tool 'Maven'
                        def mavenCMD = "${mvnHome}/bin/mvn"

                        sh "${mavenCMD} deploy -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true"
                    }
                }
            }
        }
    }

    post {
        always {
            // Clean up steps if necessary
        }

        success {
            echo 'Build and deployment successful!'
        }

        failure {
            echo 'Build or deployment failed!'
        }
    }
}
