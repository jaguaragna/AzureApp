pipeline {
   agent any
    options {
        timeout(time: 10, unit: 'MINUTES') 
    }
   stages{
        stage ('Pull Modifications') {
          steps {
           echo 'pull'
            }
        }
        stage ('Create local app via docker'){
            agent {label:'DockerContinousIntegration'}
          steps {
              dir ('/home/vagrant/AzureApp') {
                sh 'docker-compose down '
                sh 'docker-compose build '
                sh 'docker-compose up -d '
              }
            }
        }
        stage ('Test app'){
          steps {

                sh 'curl http://192.168.99.104:8080'
            }
        }
        stage ('Deploy App to Azure'){
            steps {
                echo 'deploy'
            }
        }
       
    }
}
