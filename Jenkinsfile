pipeline {
    agent any

    stages {
        stage('Build Image') {
            steps {
                script {
                    // Build Docker image using the Dockerfile in the root directory with a proper tag
                    def image = docker.build('my_image:v1') // Use a valid image name and tag
                }
            }
        }

        stage('Publish Image') {
            steps {
                script {
                    // Log in to Docker Hub ('docker_hub_login' is your actual credentials ID)
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        // Push the Docker image to Docker Hub with the correct image name and tag
                        docker.image('my_image:v1').push() // Use the same image name and tag as above
                    }
                }
            }
        }
    }
}
