pipeline {

    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/diyajindal7/devops-website-project.git'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop website-container || true'
                sh 'docker rm website-container || true'
            }
        }

        stage('Remove Old Image') {
            steps {
                sh 'docker rmi devops-website || true'
            }
        }

        stage('Build New Docker Image') {
            steps {
                sh 'docker build -t devops-website .'
            }
        }

        stage('Deploy New Container') {
            steps {
                sh 'docker run -d -p 8081:80 --name website-container devops-website'
            }
        }
    }
}