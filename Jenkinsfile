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
        echo "Folder was created..."
        // withCredentials([sshUserPrivateKey(credentialsId: 'Deploy-tomcat')]) {
        //   sh 'ssh -o StrictHostKeyChecking=no forum-deployer@192.168.0.6 "mkdir forums; \
        //        cd forums;"'
        // }
        
        sshagent(credentials : ['into-tomcat']) {
            sh 'ssh -o StrictHostKeyChecking=no forum-deployer@192.168.0.6 uptime'
            sh 'ssh -v forum-deployer@192.168.0.6'
            
            sh "mkdir -p forums && cd forums; \
                git pull origin main;"
            // sh 'scp ./source/filename user@hostname.com:/remotehost/target'
        }
        
      }
    }
  }
}