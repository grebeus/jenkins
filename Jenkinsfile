pipeline {
  agent {
      node {
          label 'slave'
          customWorkspace 'F:\MsDP\DevOps\Jenkins'
      }
  }
    stage('Checkout external proj') {
        steps {
            git branch: 'master',
                url: 'https://github.com/grebeus/naukma.git'
        }
    }
}
