
pipeline {
    agent any

    stages {
        stage('Build Image') {
            steps {
                script {
                    // Build Docker image using a valid image name and tag
                    def image = docker.build('-sklearn_website:v1')
                }
            }
        }

        stage('Publish Image') {
            steps {
                script {
                    // Log in to Docker Hub (replace 'dockerhub_credentials' with your actual credentials ID)
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        // Push the Docker image to Docker Hub with the correct image name and tag
                        docker.image('-sklearn_website:v1').push()
                    }
                }
            }
        }
    }
}
