pipeline {
  
  agent any
 
  stages {
    
    stage("build") {
      
      steps {
        echo "buidling application"
      }
    }
    stage("test") {
      when{
        expression{
          BRANCH_NAME == "main"
        }
      }
      steps {
      echo "testiing application"

      }
    }
    stage("deploy") {
      
      steps {
       echo "deploy application"

      }
    }
  }
}
