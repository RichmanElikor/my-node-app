pipeline {
  agent any

  stages {
    stage('Clone Repository') {
      steps {
        git 'https://github.com/RichmanElikor/my-node-app.git'
      }
    }

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
          sh 'docker run -d -p 3000:3000 --name my-node-app-contaner my-node-app '
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


