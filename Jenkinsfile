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
      steps {
        bat "dotnet build 'Search Engines\\Lab 2. Boolean\\Lab 2. Boolean.csproj'"
      }
    }
  }
  post {
    always {
      emailext body: 'Build completed', recipientProviders: ['sergii_grebenovych@epam.com'], subject: 'Build Notification'
    }
  }
}
