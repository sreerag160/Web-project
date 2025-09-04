pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the repository
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image with tag 'web-project'
                    docker.build('web-project')
                }
            }
        }
        stage('Test Docker Image') {
            steps {
                script {
                    // Run the Docker container in detached mode
                    def container = docker.image('web-project').run('-d -p 8080:80')
                    // Wait for a few seconds to let the container start
                    sleep 10
                    // Stop the container after test
                    container.stop()
                }
            }
        }
    }
}
