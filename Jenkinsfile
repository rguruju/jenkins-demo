pipeline {
  agent {
    label 'vagrant'
  }
  steps {
    stage('Build') {
      steps {
        git 'https://github.com/rguruju/jenkins-demo.git'
        wrap([$class: 'BuildUser']) {
          sh './gradlew clean build uploadArchives -PbuildNumber=${BUILD_NUMBER} -Pusername=${BUILD_USER_ID}'
        }
        publishHTML(
          [allowMissing: true,
          alwaysLinkToLastBuild: true,
          keepAll: true,
          reportDir: 'build/reports/tests/test',
          reportFiles: 'index.html',
          reportName: 'UnitTestReport',
          reportTitles: ''])
      }
    }
  }
}
