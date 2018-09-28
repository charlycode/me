pipeline {
  agent any
  stages {
    stage('install') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'npm test'
          }
        }
        stage('email') {
          steps {
            emailext(subject: 'Aprobar', attachLog: true, body: 'por favor aprobar', to: 'tester1')
          }
        }
      }
    }
    stage('Aprove') {
      steps {
        input(message: 'Aprobar', submitter: 'tester1')
      }
    }
    stage('email2') {
      steps {
        emailext(subject: 'Aprobar2', body: 'Aprobar please', attachLog: true, to: 'user1')
      }
    }
    stage('deploy') {
      steps {
        input(message: 'deploy', submitter: 'user1')
      }
    }
  }
}