pipeline {
 
  agent {
        docker {
            image 'maven:3-alpine'
            args '-v $HOME/.m2:/root/.m2'
        }
    }

  stages {
       stage('Tests') {
        dir('src/test/java/com/frameworkium/integration/restfulbooker/api/tests/') {
            restAssured()
        }
       }
    stage('Test') {

      steps{
       
        sh 'mvn --version'

        sh 'mvn clean test'
        
      }

    }

    stage('Results') {

      steps{
  
        //junit '**/target/*.xml'
        // mvn allure:report 

        //archiveArtifacts 'target/*'

      }

    }

  }

}