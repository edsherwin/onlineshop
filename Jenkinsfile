node{

    stage('SCM Checkout')
    {
        git 'https://github.com/edsherwin/onlineshop.git'
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
