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
        sh script: 'yarn', label: 'Install dependencies'
      }
    }
    stage('Tests') {
      steps {
        sh script: 'yarn run test:ci', label: 'Unit Tests'

        labelledShell label: 'Unit Tests', script: 'yarn run test:ci'

        sh '''
          echo "Unit Tests"
          yarn run test:ci
        '''
      }
    }
  }
  post {
    always {
      junit 'reports/**/*.xml'
    }
  }
}