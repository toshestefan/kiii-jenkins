pipeline {
  agent any
  stages {
    stage('first commit') {
      steps {
        sh '''ls-l
'''
      }
            stage('Clone repository') {
        checkout scm
    }
      stage('Build image') {
       app = docker.build("toshestefan/kiii-jenkins")
    }
     stage('Push image') {   
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
            // signal the orchestrator that there is a new version
        }
    }
    }
    

  }
}
