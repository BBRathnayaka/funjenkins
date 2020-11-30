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
        }
      }
    }
  }
}
