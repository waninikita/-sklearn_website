pipeline {
    agent any
    
    stages {
        stage('Download code from GitHub') {
            steps {
                git "https://github.com/waninikita/-sklearn_website.git"
            }
        }
        
        stage('Build Docker image') {
            steps {
                script {
                    try {
                        sh "docker build -t nikita617/nmp_jenkins:1 . --load"
                    } catch (Exception e) {
                        error "Failed to build Docker image: ${e.message}"
                    }
                }
            }
        }
        
        stage('Docker login') {
            steps {
                script {
                    try {
                        withCredentials([usernamePassword(credentialsId: 'docker_hub_login', passwordVariable: 'xyz', usernameVariable: 'nmp')]) {
                            sh "docker logout"
                            sh "echo ${xyz} | docker login -u ${nmp} --password-stdin"
                        }
                    } catch (Exception e) {
                        error "Failed to login to DockerHub: ${e.message}"
                    }
                }
            }
        }
        
        stage('Push image to DockerHub') {
            steps {
                script {
                    try {
                        sh "docker push nikita617/nmp_jenkins:1"
                    } catch (Exception e) {
                        error "Failed to push Docker image to DockerHub: ${e.message}"
                    }
                }
            }
        }
    }
}
