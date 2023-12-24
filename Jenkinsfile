pipeline {
  agent any
  triggers { pollSCM ('* * * * *')}  
  environment {
      NEXUS_URL = "https://nexus-test.belarus-devops.app/repository/helm-test/"
  }
  
  stages {

    stage("k8s") {
      steps { 
        sh "kubectl get nodes"
      }
    }
    
    stage("nexus") {
      steps { 
        sh "helm package ."
        sh "curl -u $env:USER_NEXUS:$env:PASSWORD_NEXUS ${NEXUS_URL} --upload-file *.tgz"
        sh "rm *.tgz"
      }
    }
    
  }
}
      

