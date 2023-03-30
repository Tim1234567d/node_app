pipeline {
  agent {label 'node-1'}
  stages {
    stage('Build docker image') {
      steps {
        sh 'sudo docker build -t eu.gcr.io/imposing-kayak-382008/node_app .'
        sh "pwd"
      }
    }
  }
}