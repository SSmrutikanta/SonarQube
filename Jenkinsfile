pipeline{
  agent any
  stages{
    stage("build"){
      steps{
        echo 'building the application....'
      }
    }
     stage("test"){
      steps{
        echo 'Testing the application....'
      }
    }
    stage("deploy"){
      steps{
        echo 'deploying the application....'
      }
    }
    stage("build and Sonarqube analysis"){
      steps{
        withSonarQubeEnv('My SonarQube Server'){
          sh 'mvn clean package sonar:sonar'
        }
      }
    }
    stage("Quality Gate"){
      steps{
        timeout(time: 1, unit: 'HOURS'){
          waitForQualityGate abortPipeline: true
        }
      }
    }
  }
}
