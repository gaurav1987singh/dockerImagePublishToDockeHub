node {
echo 'Building Apache Docker Image'

def ddockeruser = "g01dy1987"
def imagename = "ubuntu:16"
def container = "apache2"

stage('Git Checkout') {
    git 'https://github.com/gaurav1987singh/dockerImagePublishToDockeHub.git'
    }
    
stage('Build Docker Imagae'){
     sh "docker build -t  ${imagename} ."
    }
    
stage('Stop Existing Container'){
     sh "docker stop ${container}"
    }
    
stage('Remove Existing Container'){
     sh "docker rm ${container}"
    }
    
stage ('Runing Container to test built Docker Image'){
    sh "docker run -dit --name ${container} -p 80:80 ${imagename}"
    }
    
stage('Tag Docker Image'){
    sh "docker tag ${imagename} ${env.dockeruser}/ubuntu:16.04"
    }

stage('Docker Login and Push Image'){
    withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'dockerpasswd', usernameVariable: 'dockeruser')]) {
    sh "docker login -u ${dockeruser} -p ${dockerpasswd}"
    }
    sh "docker push ${dockeruser}/ubuntu:16.04"
    }

}
