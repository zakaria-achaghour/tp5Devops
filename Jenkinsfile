pipeline {  
  environment {
      registry = "zakariaachaghour/tp5devops"
      registryCredential = 'zakariaachaghour_DOCKER_HUB'
      dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
          git 'https://github.com/zakaria-achaghour/tp5Devops.git'
      }
    }
    stage('Building image') {
      steps{
          script {
              dockerImage = docker.build registry + ":$BUILD_NUMBER"
          }
      }
    }
    stage('Test image') {
      steps{
        script {

          echo "Tests passed"
        }
      }
    }
    stage('Publish Image') {
      steps{
          script {
              docker.withRegistry( '', registryCredential ) {
              dockerImage.push()
              }
          }
      }
    }
  }
}