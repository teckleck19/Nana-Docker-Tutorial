def nodeImage

pipeline {
  
  agent any

  environment {
    AWS_CREDS = credentials('aws-credentials')
    PATH = "$PATH:/usr/local/bin"
  }

  stages {
    
    stage("Tooling versions") {
      
      steps {
        sh '''
        /usr/local/bin/docker version
          /usr/local/bin/docker compose version
          /usr/local/bin/docker context ls
          
        '''
      }
    }
    
    stage("Deploy") {
      steps{
        sh '/usr/local/bin/docker context use myecscontext'
        sh '/usr/local/bin/docker compose up'
        sh '/usr/local/bin/docker compose ps --format json'
      }   
    }
  }
}
