def nodeImage

pipeline {
  


  agent any

  parameters{
    string(name: 'tag', defaultValue: 'latest', description: 'tag for image')
  }
  stages {
    
    stage("Build image") {
      
      steps {
        echo "buidling docker image"
        script{
           echo 'Starting to build docker image'

                script {
                  nodeImage = docker.build("750254998438.dkr.ecr.ap-southeast-1.amazonaws.com/nana-tutorial:${params.tag}")
                }
        }
      }
    }
    
    stage("Push Image") {

      steps {
        echo "pushing image to ECR in AWS"
        script{
          withDockerRegistry(credentialsId: 'ecr:ap-southeast-1:aws-credentials', url: 'https://750254998438.dkr.ecr.ap-southeast-1.amazonaws.com/nana-tutorial') {
              nodeImage.push()
          }
        }

      }
    }

    stage("deploy") {
      
      steps {
       echo "deploy application"

      }
    }
  }
}
