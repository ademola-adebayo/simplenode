pipeline {
  agent any
  tools {nodejs "node"}
  stages {
    stage('Build') {
      steps {
        echo "Building...."
        sh 'npm install'
       }
    }

    stage('Test') {
      steps {
        sh("npm test")
      }
    }

    stage('Deploy') {
      steps {
        echo "Deploying..."
      }
    }
  }
}