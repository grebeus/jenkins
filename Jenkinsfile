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
        bat "dotnet build \"Search Engines\\Lab 1. Dictionary\\Lab 1. Dictionary.csproj\""
      }
    }
  }
  post {
    always {
      emailext to: 'sergii_grebenovych@epam.com', 
               body: 'Build completed', 
               recipientProviders: [[$class: 'DevelopersRecipientProvider']], 
               subject: 'Jenkins Notification'
    }
  }
}
