pipeline {
    
    agent any

    environment {
      registry = 'localhost:5000/jenkins/funplayjenkins-prod'
      dockerImage = ''
    }

    stages {
          
      stage('Checkout Source') {
        steps {
                  git branch: 'prod', url: 'https://github.com/BBRathnayaka/funjenkins.git'
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
          sh 'docker rm -f funplayjenkins-prod'
          sh 'docker run --name funplayjenkins-prod -d -p 8888:80 localhost:5000/jenkins/funplayjenkins-prod'
          sh 'echo "Devloped here: http://localhost:8888/ "'
          }
      }
    }
  }
