pipeline {
    agent any
    environment {
        DOCKER_IMAGE = "ngtthai/lab01"
        DOCKER_CREDENTIAL = credentials('dockerhub-credential')
    }
    stages {
        stage('Git Stage') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-credential',
                    url: 'https://github.com/ThaiNguyen86/CloudHCMUS_Lab01_FE.git'
            }
        }
        stage('Build Image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}:${env.BUILD_NUMBER}")
                }
            }
        }
        stage('Push Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credential') {
                        docker.image("${DOCKER_IMAGE}:${env.BUILD_NUMBER}").push()
                        docker.image("${DOCKER_IMAGE}:${env.BUILD_NUMBER}").push('latest')
                    }
                }
            }
        }
    }
}
