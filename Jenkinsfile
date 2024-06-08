pipeline {
    agent any

    stages {
        stage('Build Image') {
            steps {
                script {
                    // Build Docker image using the Dockerfile in the root directory with a proper tag
                    def image = docker.build('-sklearn_website:v1', '.')
                }
            }
        }

        stage('Publish Image') {
            steps {
                script {
                    // Log in to Docker Hub ('docker_hub_login' is your actual credentials ID)
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        // Push the Docker image to Docker Hub with the correct image name and tag
                        docker.image('-sklearn_website:v1').push()
                    }
                }
            }
        }
    }
}
