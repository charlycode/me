pipeline {
  agent any
  stages {
    stage('install') {
      steps {
        sh 'nmp install'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
  }
}