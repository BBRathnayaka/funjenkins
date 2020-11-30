pipeline {
  
  agent any

  environment {
    registry1 = 'localhost:5000/jenkins/funplayjenkins'
    registry2 = 'localhost:5000/jenkins/funplayjenkins-prod'
    dockerImage = ''
  }

  stages {  
    stage ('Main Stage') when{ branch 'main'} {
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

      stage('Build image') {
        steps {
          echo 'HEllo'

        }
      }
  }


  // stages { 
        
  //   stage('main-branch-stuff'){
  //     agent any
  //     when{ branch 'main'}
  //       steps {
  //         echo 'run this stage - ony if the branch = main branch'
  //         echo 'Checkout Source---------------------------------'
  //         git branch: 'main', url: 'https://github.com/BBRathnayaka/funjenkins.git'
  //         echo 'Build Image Main---------------------------------'
  //         script {
  //           dockerImage = docker.build registry1
  //           docker.withRegistry( "" ) {
  //             dockerImage.push()
  //           }
  //         }
  //         echo 'Deploy App Main---------------------------------'
  //         sh 'docker rm -f funplayjenkins'
  //         sh 'docker run --name funplayjenkins -d -p 8888:80 localhost:5000/jenkins/funplayjenkins'
  //         sh 'echo "Devloped here: http://localhost:8888/ "'  
  //       }
  //   }

  //   stage('prod-branch-stuff'){
  //     agent any
  //     when{ branch 'prod'}
  //       steps {
  //         echo 'run this stage - ony if the branch = main branch'
  //         echo 'Checkout Source---------------------------------'
  //         git branch: 'prod', url: 'https://github.com/BBRathnayaka/funjenkins.git'
  //         echo 'Build Image Production---------------------------------'
  //         script {
  //           dockerImage = docker.build registry2
  //           docker.withRegistry( "" ) {
  //             dockerImage.push()
  //           }
  //         }
  //         echo 'Deploy App Production---------------------------------'
  //         sh 'docker rm -f funplayjenkins-prod'
  //         sh 'docker run --name funplayjenkins-prod -d -p 8899:80 localhost:5000/jenkins/funplayjenkins-prod'
  //         sh 'echo "Devloped here: http://localhost:8899/ "'
  //       }
  //   }

  // }
}
