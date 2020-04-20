node{

    stage('Checkout')  
    {
        git 'https://github.com/edsherwin/onlineshop.git'
    } 

    stage('Sonar Scan Code')
    {
        docker.image('my-scanner-new').inside('-v /var/run/docker.sock:/var/run/docker.sock --entrypoint=""') {
        sh "/usr/local/bin/sonar-scanner"
        }
    }

    stage('Run Docker Compose File')
    {
        sh 'sudo docker-compose build'
        sh 'sudo docker-compose down'
        sh 'sudo docker-compose up -d'
    }
    
    stage('Push Docker Image to HUB')
    {
        sh 'sudo docker push edsherwin/deployapp_web'
    }
    
}
