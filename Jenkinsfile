pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
      sh 'npm install'
      }
    }
    stage('Deploy') {
      steps {
        pushToCloudFoundry(target: 'api.run.pivotal.io', organization: 'mith-org', cloudSpace: 'development', credentialsId: 'mithcf')
      }
    }
  }
}
