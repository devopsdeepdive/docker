pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('darinpope-dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t devopsdeepdive/dp-alpine:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push devopsdeepdive/dp-alpine:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
