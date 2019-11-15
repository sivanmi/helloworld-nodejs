pipeline {
  agent { label "nodejs-app" }
  stages {
    stage('Build') {
      steps {
        container ('nodejs') {
          sh 'npm install'
        } 
      }
    }
    stage('BlackDuck') {
      steps {
        container ('synopsysdetect') {
          synopsys_detect detectProperties: '', returnStatus: true
        }
      }
    }
    stage('Deploy') {
      steps {
        pushToCloudFoundry(target: 'api.run.pivotal.io', organization: 'mith-org', cloudSpace: 'development', credentialsId: 'mithcf')
      }
    }
  }
}
