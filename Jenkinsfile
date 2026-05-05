ipeline {

agent any

environment {

DOCKER_IMAGE = 'python-hi:latest' // Docker image name

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

sh "docker build -t ${env.DOCKER_IMAGE} ."

} else {

error "Dockerfile not found in the workspace. Please create one for your Python application."

}

}

}
