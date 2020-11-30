pipeline {
  
  agent any

  environment {
    registry = 'localhost:5000/jenkins/funplayjenkins'
    dockerImage = ''
  }

  stages { 
        
    stage('main-branch-stuff'){
      agent any
      when{ branch 'prod'}
        steps {
          echo 'run this stage - ony if the branch = main branch'
          echo 'Checkout Source---------------------------------'
          git branch: 'main', url: 'https://github.com/BBRathnayaka/funjenkins.git'
          echo 'Build Image---------------------------------'
          script {
            dockerImage = docker.build registry
            docker.withRegistry( "" ) {
              dockerImage.push()
            }
          }
          echo 'Deploy App---------------------------------'
          sh 'docker rm -f funplayjenkins'
          sh 'docker run --name funplayjenkins -d -p 8888:80 localhost:5000/jenkins/funplayjenkins'
          sh 'echo "Devloped here: http://localhost:8888/ "'  
        }
    }

  }
}
