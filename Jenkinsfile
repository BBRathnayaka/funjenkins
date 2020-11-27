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
          sh '''C=prod-site
          R=$(docker inspect --format="{{ .State.Running }}" $C 2> /dev/null)

          if [$? -eq 1 ]; then
            echo "\'$C\' does not exixt."
          else
            docker rm -f $C
          fi

            #run the container
            echo ""
            docker run --name prod-site -d -p 8899:80 localhost:5000/jenkins/funplayjenkins-prod
            echo ""
              echo "Developed here: http://localhost:8899/ "
              '''
          }
      }
    }
  }
