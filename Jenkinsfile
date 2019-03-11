pipeline {
  agent {
    docker {
      image 'node:10-alpine'
    }
  }
  environment {
    CI = 'true'
    JEST_JUNIT_OUTPUT = './reports/jest/junit.xml'
  }
  stages {
    stage('Install') {
      steps {
        sh 'yarn'
      }
    }
    stage('Tests') {
      steps {
        sh {
          script 'yarn run test:ci'
          label 'Unit Tests'
        }
      }
    }
  }
  post {
    always {
      junit 'reports/**/*.xml'
    }
  }
}