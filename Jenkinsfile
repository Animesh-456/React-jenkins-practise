pipeline {
  agent any

  tools {
    nodejs "node18"
  }

  stages {
    stage('Clone repo') {
      steps {
        git 'https://github.com/Animesh-456/React-jenkins-practise.git'
      }
    }

    stage('Install dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Build React app') {
      steps {
        sh 'npm run build'
      }
    }

    stage('Deploy to EC2') {
      steps {
        sh '''
          rm -rf /var/www/html/*
          cp -r build/* /var/www/html/
        '''
      }
    }
  }
}
