pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        dotnetBuild()
      }
    }

    stage('test') {
      steps {
        bat 'dotnet add package JUnitTestLogger --version 1.1.0  '
      }
    }

  }
}