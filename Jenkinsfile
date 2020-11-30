pipeline {
  
  agent any

  environment {
    registry1 = 'localhost:5000/jenkins/funplayjenkins'
    registry2 = 'localhost:5000/jenkins/funplayjenkins-prod'
    dockerImage = ''
  }

  stages {  
    stage ('Production Branch'){
      when{ branch 'prod'}
      steps {
        script {

            stage('Checkout Source') {
              git branch: 'prod', url: 'https://github.com/BBRathnayaka/funjenkins.git'
            }

            stage('Build image') {
              script {
                dockerImage = docker.build registry2
              }
            }

            stage('Push Image') {
              script {
                docker.withRegistry( "" ) {
                  dockerImage.push()
              }
            }
          }

            stage('Deploy App') {
              sh 'docker rm -f funplayjenkins-prod'
              sh 'docker run --name funplayjenkins-prod -d -p 8899:80 localhost:5000/jenkins/funplayjenkins-prod'
              sh 'echo "Devloped here: http://localhost:8899/ "'
          }

        }
      }
    }

    stage ('Main Branch'){
      when{ branch 'main'}
      steps {
        script {

            stage('Checkout Source') {
              git branch: 'main', url: 'https://github.com/BBRathnayaka/funjenkins.git'
            }

            stage('Build image') {
              script {
                dockerImage = docker.build registry1
              }
            }

            stage('Push Image') {
              script {
                docker.withRegistry( "" ) {
                  dockerImage.push()
              }
            }
          } 

            stage('Deploy App') {
              sh 'docker rm -f funplayjenkins'
              sh 'docker run --name funplayjenkins-prod -d -p 8888:80 localhost:5000/jenkins/funplayjenkins'
              sh 'echo "Devloped here: http://localhost:8888/ "'
          }

        }
      }
    }
    
    // stage ('Production Branch'){
    //   when{ branch 'prod'}
    //   steps {
    //     script {
    //       stage ('Stage 1') {
    //         sh 'echo Stage 1'
    //       }
    //       stage ('Stage 2') {
    //         sh 'echo Stage 2'
    //       }
    //       stage ('Stage 3') {
    //         sh 'echo Stage 3'
    //       }
    //     }
    //   }
    // }
  }
}
