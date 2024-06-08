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
                    // Log in to Docker Hub ('docker_hub_login')
                    docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_login') {
                        // Push the Docker image to Docker Hub with the correct image name and tag
                        docker.image('nikita617/docker_image:latest').push()
                    }
                }
            }
        }
    }
}
