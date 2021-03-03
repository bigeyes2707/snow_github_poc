pipeline {
  agent any
  environment {
    APPSYSID = '0713cd811b66a4d487ee76eecc4bcbe0'
    BRANCH = "${BRANCH_NAME}"
    CREDENTIALS = 'servicenow'
    DEVENV = 'https://comcastdemo.service-now.com/'
    TESTSUITEID = 'b1ae55eedb541410874fccd8139619fb'
  }
  stages {
    stage('Build') {
      when {
        not {
          branch 'master'
        }
      }
      steps {
        snApplyChanges(appSysId: "${APPSYSID}", branchName: "${BRANCH}", url: "${DEVENV}", credentialsId: "${CREDENTIALS}")
        snPublishApp(credentialsId: "${CREDENTIALS}", appSysId: "${APPSYSID}", obtainVersionAutomatically: true, url: "${DEVENV}")
      }
  }
}
