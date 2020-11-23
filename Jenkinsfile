pipeline {
  agent {
      node {
          label 'slave'
      }
  }
    stage('Checkout external proj') {
        steps {
            git branch: 'master',
                url: 'https://github.com/grebeus/naukma.git'
        }
    }
}
