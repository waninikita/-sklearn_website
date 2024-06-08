pipeline {
    agent any

    stages {
        stage('Build Image') {
            steps {
                script {
                    // Build Docker image using the Dockerfile in the root directory with a proper tag
                    def image = docker.build('python_app:tag')
                }
            }
        }

        stage('Publish Image') {
            steps {
                script {
                    // Log in to Docker Hub (replace 'docker_hub_login' with your actual credentials ID)
                    docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_login') {
                        // Push the Docker image to Docker Hub with the correct image name and tag
                        docker.image('python_app:tag').push()
                    }
                }
            }
        }
    }
}
