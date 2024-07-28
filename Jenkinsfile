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

        // stage('Build Docker Image') {
        //     steps {
        //         script {
        //             docker.build(DOCKERHUB_REPOSITORY)
        //         }
        //     }
        // }

        // stage('Push Docker Image') {
        //     steps {
        //         script {
        //             docker.withRegistry('https://index.docker.io', DOCKER_CREDENTIALS_ID) {
        //                 docker.image(DOCKERHUB_REPOSITORY).push('latest')
        //             }
        //         }
        //     }
        // }

        // stage('Deploy Docker Container') {
        //     steps {
        //         script {
        //             sh '''
        //             docker run -d --name java-app --rm $DOCKERHUB_REPOSITORY:latest
        //             '''
        //         }
        //     }
        // }
    }
}
