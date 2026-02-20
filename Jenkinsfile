
pipeline {
//  agent {label 'Agent1'}
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Build') {
      steps {
        bat 'echo "Hello world"'
      }
    }
    stage ('cat README') {
      when {
        branch {fix-*}
      }
      steps {
        bat 'cat README.md'
      }
  }
  post {
    always {
        junit(
          allowEmptyResults: true, 
          testResults: '**/build/test-results/test/*.xml'
        )
    }
  }
}
