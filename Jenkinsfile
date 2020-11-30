pipeline {
  
  agent any

  environment {
    registry = 'localhost:5000/jenkins/funplayjenkins'
    dockerImage = ''
  }

  stages {
        
    stage('Checkout Source') {
      steps {
                git branch: 'main', url: 'https://github.com/BBRathnayaka/funjenkins.git'
            }
    }

    stage('master-branch-stuff'){
    agent any
    when{ branch 'prod'}
      steps {
        echo 'run this stage - ony if the branch = master branch'
      }
    }


    stage('Build image') {
      steps {
        script {
          dockerImage = docker.build registry
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

      post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
