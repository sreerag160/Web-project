pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sreerag160/Web-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t web-project .'
                }
            }
        }

        stage('Deploy Container') {
            steps {
                script {
                    sh '''
                        docker stop web-project-container || true
                        docker rm web-project-container || true
                        docker run -d -p 9090:80 --name web-project-container web-project
                    '''
                }
            }
        }
    }
}
