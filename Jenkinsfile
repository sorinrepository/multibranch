
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
    stage ('echo README') {
      when {
        branch "fix-*"
      }
      steps {
        bat 'echo README.md'
      }
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
