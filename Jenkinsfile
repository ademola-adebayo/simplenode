pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        echo "Building...."
        // sh("npm install")
       }
    }

    stage('Test') {
      steps {
        sh("npm run test")
      }
    }

    stage('Deploy') {
      steps {
        echo "Deploying..."
      }
    }
  }
}