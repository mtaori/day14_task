pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'docker'
        DOCKERHUB_REPOSITORY = 'mtaori/javaimage:v10'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mtaori/day14_task.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    def customImage = docker.build("${env.DOCKERHUB_REPOSITORY}")
                    docker.withRegistry('https://index.docker.io/v1/', "${env.DOCKER_CREDENTIALS_ID}") {
                        customImage.push()
                    }
                }
            }
        }

        stage('Run Docker Image') {
            steps {
                script {
                    // Run the Docker container from the image
                    docker.image("${env.DOCKERHUB_REPOSITORY}").inside {
                        sh 'java App' 
                    }
                }
            }
        }
    }
}
