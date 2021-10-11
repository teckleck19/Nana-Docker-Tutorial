def nodeImage

pipeline {
  
  agent any

  environment {
    AWS_CREDS = credentials('aws-credentials')
  }

  stages {
    
    stage("Tooling versions") {
      
      steps {
        sh '''
          #!/bin/bash
          docker --version
          docker-compose --version
        '''
      }
    }
    
    stage("Deploy") {
      steps{
        sh "#!/bin/bash"
        sh 'docker context use myecscontext'
        sh 'docker-compose up'
        sh 'docker-compose ps --format json'
      }   
    }
  }
}
