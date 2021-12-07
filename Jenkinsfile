pipeline {
  agent any
  tools {nodejs "nodejs"}
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
        sh 'ssh -o StrictHostkeyChecking=no forum-deployer@192.168.0.6 "mkdir forum; \
        cd forum; \
        git pull origin main; "'
      }
    }
  }
}