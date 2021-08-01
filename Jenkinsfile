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
        dotnetTest(logger: '\\"junit;LogFilePath=\\"${WORKSPACE}\\"/TestResults/1.0.0.\\"${env.BUILD_NUMBER}\\"/results.xml\\" --configuration release --collect \\"Code coverage\\""')
      }
    }

  }
}