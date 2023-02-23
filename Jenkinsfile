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
        stage ('Cleanup WorkSpace') {
            script {
                cleanWs()
            }
        }
    }
}
