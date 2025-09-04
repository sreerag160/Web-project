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
                    bat 'docker build -t web-project .'
                }
            }
        }

        stage('Deploy Container') {
            steps {
                script {
                    bat '''
                        docker stop web-project-container || exit 0
                        docker rm web-project-container || exit 0
                        docker run -d -p 9090:80 --name web-project-container web-project
                    '''
                }
            }
        }
    }
}
