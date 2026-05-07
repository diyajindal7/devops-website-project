pipeline {

    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build --no-cache -t devops-website .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop website-container || true'
                sh 'docker rm website-container || true'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker run -d -p 8081:80 --name website-container devops-website'
            }
        }
    }
}