pipeline {
  agent any

  tools {
    nodejs "node18" // Make sure this matches your Node.js version name in Jenkins
  }

  environment {
    DEPLOY_DIR = "/home/ubuntu/sites/React-jenkins-practise"
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/Animesh-456/React-jenkins-practise.git' // Replace with your actual repo
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Build React App') {
      steps {
        sh 'npm run build'
      }
    }

    stage('Deploy Build Folder') {
      steps {
        sh '''
          echo "Cleaning up old build..."
          rm -rf $DEPLOY_DIR/build
          echo "Copying new build..."
          cp -r build $DEPLOY_DIR/
        '''
      }
    }

    stage('Restart PM2') {
      steps {
        sh 'pm2 reload 0' // Assuming your app is managed by PM2 and the process ID is 0
      }
    }
  }
}
