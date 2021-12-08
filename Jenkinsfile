pipeline {
  agent any
  tools {nodejs "nodejs"}
  stages {
    stage('Prepare environment') {
      steps {
        echo "Building...."
        git branch: 'main', url: 'https://github.com/ademola-adebayo/simplenode.git'
        sh 'npm install'
       }
    }

    stage('Code analyse') {
      steps {
        echo "Building...."
        sh 'echo "Run some lints"'
       }
    }

    stage('Unit test') {
      steps {
        echo "Unit testing...."
        sh 'echo "Tests will back"'
       }
    }

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
        
        sh 'ssh forum-deployer@192.168.0.6 rm -rf get-here/temp_deploy/dist'
        sh 'ssh forum-deployer@192.168.0.6 mkdir -p check/new/path/temp_deploy'
        sh 'scp -r ~/distin forum-deployer@192.168.0.6:~/check/new/path/dist/'
        sh 'ssh forum-deployer@192.168.0.6 "mv check/new/path/dist/ get-here/temp_deploy/"'
      }
    }
  }
}