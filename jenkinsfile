pipeline {
  agent any

  stages {
    stage('Clone Repository') {
      steps {
        git 'https://github.com/YOUR_USERNAME/my-node-app.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          docker.build("my-node-app")
        }
      }
    }

    stage('Run Docker Container') {
      steps {
        script {
          def container = docker.run("my-node-app", "-p 3000:3000", "--rm", true)
          echo "Running container..."
        }
      }
    }
  }
}
