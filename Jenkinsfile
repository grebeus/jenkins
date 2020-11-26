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
    stage('Build .NET proj and scan') {
      steps { 
        withSonarQubeEnv('My SonarQube Server') {
          bat "dotnet-sonarscanner begin /k:\"sonarkey\" /d:sonar.host.url=\"http://172.21.203.210:9000\" /d:sonar.login=\"476495d6e6bcd25c58b84f10d76d978b0213239d\""
          bat "dotnet build \"Search Engines\\Lab 1. Dictionary\\Lab 1. Dictionary.csproj\""
          bar "dotnet-sonarscanner end /d:sonar.login=\"476495d6e6bcd25c58b84f10d76d978b0213239d\""
        }
      }
    }
    stage("Quality Gate") {
        steps {
            waitForQualityGate abortPipeline: true
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
