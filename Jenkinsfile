pipeline {
  agent {
    docker {
      image 'node:10-alpine'
    }
  }
  environment {
    CI = 'true'
  }
  stages {
    stage('Install') {
      steps {
        sh 'yarn'
      }
    }
    stage('Tests') {
      steps {
        sh 'yarn run test:ci'
      }
    }
  }
  post {
    always {
      junit 'reports/**/*.xml'
    }
  }
}