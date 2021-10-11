def nodeImage

pipeline {
  
  agent any

  environment {
    AWS_CREDS = credentials('aws-credentials')
    PATH = "$PATH:/usr/bin/local"
  }

  stages {
    
    stage("Tooling versions") {
      
      steps {
        sh '''
          #!/bin/bash
          echo $PATH
          which docker
          docker-compose --version
          docker context create ecs myecscontext --from-env
          docker context ls
          
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
