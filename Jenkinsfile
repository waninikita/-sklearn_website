pipeline {
    agent any

    stages {
        stage('Build Image') {
            when {
                branch 'master'  // Only run this stage on the master branch
            }
            steps {
                script {
                    // Build Docker image using the Dockerfile in the root directory with a proper tag
                    def image = docker.build('my_image:latest')
                }
            }
        }

        stage('Publish Image') {
            when {
                branch 'master'  // Only run this stage on the master branch
            }
            steps {
                script {
                    // Log in to Docker Hub (replace 'dockerhub_credentials' with your actual credentials ID)
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        // Push the Docker image to Docker Hub with the correct image name and tag
                        docker.image('my_image:latest').push()
                    }
                }
            }
        }
    }
}
