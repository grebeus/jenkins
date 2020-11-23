pipeline {
  agent {
      node {
          label 'slave'
      }
  }
  stages {
    stage('Checkout proj') {
      steps {
          git branch: 'master',
              url: 'https://github.com/grebeus/naukma.git'
      }
    }
    stage('Build .NET proj') {
      
    }
  }
  post {
    always {
      emailext body: 'Build completed', recipientProviders: 'sergii_grebenovych@epam.com', subject: 'Build Notification'
    }
  }
}
