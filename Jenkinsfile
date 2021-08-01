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
        powershell 'dotnet add package JUnitTestLogger --version 1.1.0  '
      }
    }

    stage('error') {
      steps {
        bat 'dotnet test --logger \\"junit;LogFilePath=\\"${WORKSPACE}\\"/TestResults/1.0.0.\\"${env.BUILD_NUMBER}\\"/results.xml\\" --configuration release --collect \\"Code coverage\\""'
      }
    }

  }
}