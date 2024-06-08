pipeline {
    agent any

    stages {
        stage('Build Image') {
            when {
                branch 'master'  // only run these steps on the master branch
            }
            steps {
                // Jenkins Stage to Build the Docker Image
                script {
                    // Build Docker image using the Dockerfile named 'Dockerfile'
                    docker.build('Dockerfile')
                }
            }
        }

        stage('Publish Image') {
            when {
                branch 'master'  // only run these steps on the master branch
            }
            steps {
                // Jenkins Stage to Publish the Docker Image to Dockerhub or any Docker repository of your choice.
                script {
                    // Log in to Docker Hub (replace 'username', 'password', and 'email' with your Docker Hub credentials)
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        // Push the Docker image to Docker Hub
                        docker.image('my_image_name').push('latest')
                    }
                }
            }
        }
    }
}
