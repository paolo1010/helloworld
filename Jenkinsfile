pipeline{
  agent any
  tools {
    maven 'M2_HOME'
  }
  environment {
    registry = "agbonnon10/devops-pipeline"
    registryCredential = 'Docker_ID2'
  }
  stages {
    stage('Build'){
      steps {
        sh 'mvn clean'
        sh 'mvn install'
        sh 'mvn package'
      }
    }
    stage('Test'){
      steps {
        echo "test step"
        sh 'mvn test'
      }
    }
    stage('Deploy'){
      steps {
        docker.build registry + ":$BUILD_NUMBER"
      }
    }
  }
}
