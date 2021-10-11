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
                    def nodeImage = docker.build("nana-tutorial:${env.BUILD_ID}")
                }
        }
      }
    }
    
    stage("Push Image") {

      steps {
        echo "pushing image to ECR in AWS"
        script{
          withDockerRegistry(credentialsId: 'ecr:ap-southeast-1:aws-credentials', url: '750254998438.dkr.ecr.ap-southeast-1.amazonaws.com/nana-tutorial') {
              nodeImage.push("${params.tag}")
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
