pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'python-hi'       // Docker image name
        CONTAINER_NAME = 'python-hi-cont'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/itissiacsd-gif/docker-py.git'
            }
        }

        stage('Docker Build') {
            steps {
                script {
                    // Check if Dockerfile exists
                    if (fileExists('Dockerfile')) {
                        sh "docker build -t ${DOCKER_IMAGE} ."
                    } else {
                        error "Dockerfile not found in the workspace."
                    }
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh """
                    docker rm -f ${CONTAINER_NAME} || true
                    docker run -d --name ${CONTAINER_NAME} ${DOCKER_IMAGE}
                    """
                }
            }
        }
    }
}
