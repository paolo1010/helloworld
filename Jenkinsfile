pipeline{
  agent any
  tools {
    maven 'M2_HOME'
  }
  environment {
    registry = "agbonnon10/development"
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
        script {
        docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
  }
}

post {
        always {
            echo "Always display this message "
        }
        failure {
            echo "Job failed "
        }
        success {
            echo "Successful run "
        }
        unstable {
            echo "The job is unstable "
        }
    }
