pipeline {
  // Remove the label from agent
  agent any
  
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('esmail1055-shaikh')
  }
  stages {
    stage('Build') {
      steps {
        sh './jenkins/build.sh'
      }
    }
    stage('Login') {
      steps {
        sh './jenkins/login.sh'
      }
    }
    stage('Push') {
      steps {
        sh './jenkins/push.sh'
      }
    }
  }
  post {
    always {
      sh './jenkins/logout.sh'
    }
  }
}

