pipeline {
  agent any

  stages {
    stage('Build Docker Image') {
      steps {
        script {
          sh 'docker build -t my-node-app .'
        }
      }
    }

    stage('Run Docker Container') {
      steps {
        script {
          sh 'docker run -d -p 3000:3000 --name my-node-app-container my-node-app '
        }
      }
    }
  }


    post {
    always {
      script {
        // Stop and remove the container after build is done 
        sh 'docker stop my-node-app-container || true'
        sh 'docker rm my-node-app-container || true'
        
      }
    }
  }
}


