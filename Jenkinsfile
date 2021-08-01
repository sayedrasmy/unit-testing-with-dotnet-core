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
        bat 'dotnet add C:\\JH\\workspace\\_testing-with-dotnet-core_master\\app  package JUnitTestLogger --version 1.1.0 '
      }
    }

    stage('Unit test') {
      steps {
        dotnetTest(logger: '\\"junit;LogFilePath=\\"${WORKSPACE}\\"/TestResults/1.0.0.\\"${env.BUILD_NUMBER}\\"/results.xml\\" --configuration release --collect \\"Code coverage\\"')
      }
    }

    stage('Covergae') {
      steps {
        bat 'CodeCoverage.exe analyze  /output:${WORKSPACE}\\\\J_testing-with-dotnet-core_master\\TestResults\\1.0.0.${env.BUILD_NUMBER}\\\\xmlresults.coveragexml  ${WORKSPACE}\\\\TestResults\\\\testcoverage.coverage'
      }
    }

    stage('Report Generator') {
      steps {
        bat 'ReportGenerator.exe -reports:${WORKSPACE}\\\\TestResults\\\\xmlresults.coveragexml -targetdir:${WORKSPACE}\\\\CodeCoverage_${env.BUILD_NUMBER}'
      }
    }

  }
}