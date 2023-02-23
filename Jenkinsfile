pipeline {
    agent any
    environment {
        DOCKERHUB_USERNAME = "shalin1000"
        APP_NAME = "web-python"
        IMAGE_TAG = "${BUILD_NUMBER}"
        IMAGE_NAME = "${DOCKERHUB_USERNAME}" + "/" + "${IMAGE_TAG}"
        REGISTRY_CREDS = 'docker-registrty'
    }

    stages {
        stage ('Cleanup Workspace') {
            steps {
                script {
                    cleanWs()
                }
            }
        }
        stage ('Git Checkout') {
            steps {
                script {
                    git credentialsId: 'GIT-PAT',
                    url: 'https://github.com/shalin-1000/python-app',
                    branch: 'main'
                }
            }

        }
        stage ('Docker Build') {
            steps {
                script {
                    docker_image = docker.build "${IMAGE_NAME}"
                }
            }
        }

        stage ('Push the Image') {
            steps {
                script {
                    docker.withRegistry('',REGISTRY_CREDS) {
                        docker_image.push("$BUILD_NUMBER")
                        docker_image.push('latest')
                    }

                }
            }
        }
    }
}
