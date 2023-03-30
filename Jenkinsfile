pipeline {
  agent {label 'node-1'}
  stages {
    stage('Build docker image') {
      steps {
        sh 'sudo docker build -t eu.gcr.io/imposing-kayak-382008/node_app .'
        sh "pwd"
      }
    }
    stage("Configure authentication") {
        steps {
            sh "gcloud auth activate-service-account baisalov-t98-gmail-com@imposing-kayak-382008.iam.gserviceaccount.com --key-file=/home/temirlan/imposing-kayak-382008-ff36b33690ea.json"
        }
    }
    stage("gcloud login") {
        steps{
            sh "gcloud auth login --cred-file=/home/temirlan/imposing-kayak-382008-ff36b33690ea.json"
        }
    }
    stage("Configure docker") {
        steps {
            sh "gcloud auth configure-docker"
        }
    }
    stage('Push to gcr') {
      steps {
        sh 'sudo docker push eu.gcr.io/imposing-kayak-382008/node_app'
      }
    }
  }
}