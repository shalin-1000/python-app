pipeline {
    agent any
    environment {
        DOCKERHUB_USERNAME = "shalin1000"
        APP_NAME = "web-python"
        IMAGE_TAG = "${BUILD_NUMBER}"
        IMAGE_NAME = "${DOCKERHUB_USERNAME}" + "/" + "${IMAGE_TAG}"
        REGISTRY_CREDS = 'docker-registry'
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
    }
}
