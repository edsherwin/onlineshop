node{

    stage('Parallel'){
        steps {
            parallel (
                'Checkout': {
                    git 'https://github.com/edsherwin/onlineshop.git'
                },
                {
                'Scan': {
                    docker.image('my-scanner-new').inside('-v /var/run/docker.sock:/var/run/docker.sock --entrypoint=""') {
                    sh "/usr/local/bin/sonar-scanner"}
                    }
                }
            )
        }
    }
    // {
    //     git 'https://github.com/edsherwin/onlineshop.git'
    // } 
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
