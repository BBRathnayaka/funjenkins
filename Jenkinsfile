pipeline {
  
  agent any

  environment {
    registry1 = 'localhost:5000/jenkins/funplayjenkins'
    registry2 = 'localhost:5000/jenkins/funplayjenkins-prod'
    dockerImage = ''
  }

  stages {  
    stage ('Main Branch'){
      when{ branch 'prod'}
      steps {
        script {
            stage ('Stage 1') {
              sh 'echo Stage 1'
            }
            stage('Checkout Source') {
              git 'https://github.com/BBRathnayaka/funjenkins.git'
          }
        }
      }
    }
    
    stage ('Production Branch'){
      when{ branch 'prod'}
      steps {
        script {
          stage ('Stage 1') {
            sh 'echo Stage 1'
          }
          stage ('Stage 2') {
            sh 'echo Stage 2'
          }
          stage ('Stage 3') {
            sh 'echo Stage 3'
          }
        }
      }
    }
  }
}
