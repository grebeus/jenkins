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
        bat "dotnet build 'Search Engines\\Lab 1.1. PostgreSQL\\Lab 1.1. PostgreSQL\\Lab 1.1. PostgreSQL.csproj"'"
      }
    }
  }
  post {
    always {
      emailext body: 'Build completed', recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Build Notification'
    }
  }
}
