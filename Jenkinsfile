pipeline {
  
  agent any

  stages {  
    stage ('Main Branch'){
      when{ branch 'main'}
      steps {
        script {
          if (true) {
            stage ('Stage 1') {
              sh 'echo Stage 1'
            }
          }
          if (false) {
            stage ('Stage 2') {
              sh 'echo Stage 2'
            }
          }
        }
      }
    }
    
    stage ('Prod Branch'){
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
          stage ('Stage 4') {
            sh 'echo Stage 4'
          }
          stage ('Stage 5') {
            sh 'echo Stage 5'
          }
        }
      }
    }
  }
}
