pipeline {
  agent {label 'node-1'}
  stages {
    stage('Build docker image') {
      steps {
        sh 'docker build -t eu.gcr.io/beaming-ion-382215/node_app .'
        sh "pwd"
        sh "whoami"
      }
    }
    stage("Configure authentication") {
        steps {
            sh "gcloud auth activate-service-account demo-572@beaming-ion-382215.iam.gserviceaccount.com --key-file=/home/temirlan/beaming-ion-382215-527e481998d1.json"
        }
    }
     stage("gcloud auth login") {
        steps{
            sh "docker login -u _json_key --password-stdin https://eu.gcr.io < /home/temirlan/beaming-ion-382215-527e481998d1.json"
        }
    }
    stage("set project"){
        steps{
            sh "gcloud config set project beaming-ion-382215"
        }
    }
    // stage("Configure docker") {
    //     steps {
    //         sh "gcloud auth configure-docker"
    //     }
    // }
    stage('Push to gcr') {
      steps {
        sh 'docker push eu.gcr.io/beaming-ion-382215/node_app'
      }
    }
  }
}