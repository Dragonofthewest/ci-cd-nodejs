pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git url: 'file:///root/ci-cd-nodejs'
      }
    }
    stage('Build') {
      steps {
        sh 'docker build -t node-app .'
      }
    }
    stage('Push') {
      steps {
        sh 'docker tag node-app localhost:5000/node-app'
        sh 'docker push localhost:5000/node-app'
      }
    }
    stage('Deploy') {
      steps {
        sh 'kubectl apply -f k8s'
      }
    }
  }
}
