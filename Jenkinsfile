    pipeline {
        agent any

        environment {
            DOCKER_CREDENTIALS_ID = 'docker'
            DOCKERHUB_REPOSITORY = 'mtaori/javaimage:v2'
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
                        checkout scm
                        def customImage = docker.build("${env.DOCKERHUB_REPOSITORY}")
                    }
                }
            }

            stage('Run Tests') {
                steps {
                    script {
                        // Run the tests inside the Docker container
                        docker.image("${env.DOCKERHUB_REPOSITORY}").inside {
                            sh 'make test'
                        }
                    }
                }
            }
        
        }
    }
