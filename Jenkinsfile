#!/usr/bin/env groovy
pipeline {
    agent any

    stages {
        stage('Build Image') {
            when {
                branch 'master'  // Only run these steps on the master branch
            }
            steps {
                script {
                    // Build Docker image
                    def image = docker.build('my_image_name')
                }
            }
        }

        stage('Publish Image') {
            when {
                branch 'master'  // Only run these steps on the master branch
            }
            steps {
                script {
                    // Log in to Docker Hub using the credentials ID you set up
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        // Push the Docker image to Docker Hub
                        def image = docker.image('my_image_name')
                        image.push('latest')
                    }
                }
            }
        }
    }
}
