pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-credentials',
                    url: 'https://github.com/AndrejGockov/kiii-jenkins-github-actions-gitlab-cicd-homework.git'
            }
        }
        stage('Build image') {
            steps {
                script {
                    docker.build("andrejgockov/kiii-jenkins-test:latest")
                }
            }
        }
        stage('Push image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        docker.image("andrejgockov/kiii-jenkins-test:latest").push()
                    }
                }
            }
        }
    }
}
