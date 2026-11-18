pipeline {
    agent {
        label('agentfarm')
       }

    stages {
        stage('Build Docker Image') {
            steps {
                sh '''sudo dnf install docker -y
                  sudo systemctl start docker
                  sudo docker build -f Dockerfile -t webserver:latest .
                  sudo docker images -a
                  '''
                       } 
                  }
       stage('Deploy Docker Image') {
            steps {
                sh '''
                  #sudo docker stop $(sudo docker container ls -aq)
                  #echo 'All containers stopped'
                  sudo docker run -d -p 80:80 webserver:latest
                  sudo docker ps -a
                  echo 'List of all containers with their current status'
                  '''
                       }
                  }
        }
 }
