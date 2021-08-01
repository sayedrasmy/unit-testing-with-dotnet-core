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
        bat 'dotnet add C:\\JH\\workspace\\_testing-with-dotnet-core_master\\app  package JUnitTestLogger --version 1.1.0   dotnet test '
      }
    }

    stage('') {
      steps {
        dotnetTest(logger: '\\"junit;LogFilePath=\\"${WORKSPACE}\\"/TestResults/1.0.0.\\"${env.BUILD_NUMBER}\\"/results.xml\\" --configuration release --collect \\"Code coverage\\"')
      }
    }

  }
}