pipeline {
    agent any

    stages {
        stage('Build Image') {
            steps {
                script {
                    // Build Docker image using the Dockerfile in the root directory with a proper tag
                    def image = docker.build('nikita617/docker_image:latest')
                }
            }
        }

        stage('Publish Image') {
            steps {
                script {
                    // Log in to Docker Hub (replace 'dockerhub_credentials' with your actual credentials ID)
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        // Push the Docker image to Docker Hub with the correct image name and tag
                        def image = docker.image('nikita617/docker_image:latest')
                        image.push()
                    }
                }
            }
        }
    }
}
