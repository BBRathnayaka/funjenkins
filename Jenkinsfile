pipeline {
  
  agent any

  stages {  
    stage ('Main Stage'){
      agent any
      when{ branch 'prod'}
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
  }
}
