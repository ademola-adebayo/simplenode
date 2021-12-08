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
        
        sh 'ssh forum-deployer@192.168.0.6 rm -rf get-here'
        sh 'ssh forum-deployer@192.168.0.6 mkdir -p get-here/temp_deploy'
        // sh 'scp -r dist forum-deployer@192.168.0.6:/get-here/temp_deploy/dist/'
        // sh 'ssh forum-deployer@192.168.0.6 "rm -rf get-here/example.com/dist/ && mv get-here/temp_deploy/dist/ get-here/example.com/"'
      }
    }
  }
}