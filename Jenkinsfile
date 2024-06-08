pipeline {
    agent any
    
    stages {
        stage('Build Image') {
            steps {
                script {
                    // Build Docker image using the Dockerfile
                    docker.build('my_image_name')
                }
            }
        }
        
        stage('Publish Image') {
            steps {
                script {
                    // Log in to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        // Push the Docker image to Docker Hub
                        docker.image('my_image_name').push('latest')
                    }
                }
            }
        }
    }
}
