pipeline{
    agent any;
    
    stages{
        stage('download code from github')
        {
            steps{
                git "https://github.com/waninikita/-sklearn_website.git"
            }
        }
        stage('docker images')
        {
            steps{
            sh    "docker build -t Nikita617/nmp_jenkins:1 .  --load"
            }
        }
        stage('docker login')
        {
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker_hub_login', passwordVariable: 'xyz', usernameVariable: 'nmp')]) {
                sh   "docker logout"    
                sh    "echo ${xyz}  | docker login -u ${nmp} --password-stdin"
                 }
                
                
            }
        }
        stage('push images to dockerhub')
        {
            steps{
             sh   "docker push Nikita617/nmp_jenkins:1"
            }
        }
    }
}    
        