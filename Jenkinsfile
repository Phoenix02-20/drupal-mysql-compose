pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker-compose pull'
        echo 'Docker-compose-build Build image completed'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        echo 'Login Completed'
      }
    }
    stage('Push') {
      steps {
        sh 'docker-compose push'
        echo 'Login Completed'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
