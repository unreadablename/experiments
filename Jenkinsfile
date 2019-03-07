pipeline {
  agent any
  stages {
    stage('Install') {
      steps {
        sh 'echo "Hello"'
      }
    }
    stage('Tests') {
      steps {
        sh '''echo "Test"
exit $(( RANDOM % 2 ))'''
      }
    }
  }
}