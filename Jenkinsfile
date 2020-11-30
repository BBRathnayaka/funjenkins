pipeline {
  
  agent any

  environment {
    registry1 = 'localhost:5000/jenkins/funplayjenkins'
    registry2 = 'localhost:5000/jenkins/funplayjenkins-prod'
    dockerImage = ''
  }

  stages {  

    stage ('Main Branch'){
        agent any
      when{ branch 'prod'}
      steps {
        script {

          stage('Checkout Source') {
            steps {
                      git branch: 'prod', url: 'https://github.com/BBRathnayaka/funjenkins.git'
                  }
          }

          stage('Build image') {
            steps {
              script {
                dockerImage = docker.build registry1
              }
            }
          }

          stage('Push Image') {
            steps {
              script {
                docker.withRegistry( "" ) {
                  dockerImage.push()
                }
              }
            }
          }

          stage('Deploy App') {
            steps {
              sh 'docker rm -f funplayjenkins'
              sh 'docker run --name funplayjenkins -d -p 8888:80 localhost:5000/jenkins/funplayjenkins'
              sh 'echo "Devloped here: http://localhost:8888/ "'
            }
          }

        }
      }
    }

    // stage ('Production Branch'){
    //     agent any
    //   when{ branch 'prod'}
    //   steps {
    //     script {

    //       stage('Checkout Source') {
    //         steps {
    //                   git branch: 'prod', url: 'https://github.com/BBRathnayaka/funjenkins.git'
    //               }
    //       }

    //       stage('Build image') {
    //         steps {
    //           script {
    //             dockerImage = docker.build registry2
    //           }
    //         }
    //       }

    //       stage('Push Image') {
    //         steps {
    //           script {
    //             docker.withRegistry( "" ) {
    //               dockerImage.push()
    //             }
    //           }
    //         }
    //       }

    //       stage('Deploy App') {
    //         steps {
    //           sh 'docker rm -f funplayjenkins'
    //           sh 'docker run --name funplayjenkins -d -p 8899:80 localhost:5000/jenkins/funplayjenkins'
    //           sh 'echo "Devloped here: http://localhost:8899/ "'
    //         }
    //       }

    //     }
    //   }
    // }
    
  }
}
