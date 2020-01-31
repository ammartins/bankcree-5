pipeline {
  agent any
  stages {
    stage('Build Docker Image - Master') {
      when {
        branch 'master'
      }
      steps {
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Build Docker Image - Release Candidate') {
      when {
        not {
          branch 'master'
        }
      }
      steps {
        script {
          dockerImage = docker.build registry + ":rc-$BUILD_NUMBER"
        }
      }
    }
    stage('Push Docker Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
  environment {
    registry = 'ammartins/bankcree-5'
    registryCredential = 'docker-hub'
  }
}
