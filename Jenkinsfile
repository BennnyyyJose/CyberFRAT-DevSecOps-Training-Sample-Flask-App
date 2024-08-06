pipeline {
  environment {
    registry = "benniyamjose/cyberfrat-devsecops"
    registryCredential = "Jenkinsdocker"
    dockerImage = ''
  }
  
  agent any
  
  stages {
    stage ('Build Docker Image') {
      steps {
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }

    Stage('Push to DockerHub')
      steps {
        script {
          docker.withRegistry('', registryCredential ) {
            docker.Image.push()
          }
        }
      }
  }
    stage('Test Run'){
      steps {
        sh 'docker run -d cyberfrat:$BUILD_NUMBER'
      }
    }
  }
}
