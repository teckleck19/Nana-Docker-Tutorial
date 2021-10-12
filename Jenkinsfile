pipeline {
  
  agent any

  environment {
    AWS_CREDS = credentials('aws-credentials')
    PATH = "/usr/local/bin:$PATH"
  }

  stages {
    
    stage("Tooling versions") {
      
      steps {
        sh '''
          docker version
          docker compose version
          docker context ls
        '''
      }
    }

    stage("Build") {
      steps{
        sh 'docker context use default'
        sh 'docker compose pull'
        sh 'docker compose build'
        sh 'docker compose push'
        
      }   
    }
    
    stage("Deploy") {
      steps{
        sh 'docker context use myecscontext'
        sh 'docker compose up'
        sh 'docker compose ps --format json'
      }   
    }
  }
}
