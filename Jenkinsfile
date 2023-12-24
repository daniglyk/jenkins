pipeline {
  agent any
  triggers { pollSCM ('* * * * *')}  
  environment {
      NEXUS_URL = "https://nexus-test.belarus-devops.app/repository/helm-test/"
  }
  
  stages {

    stage("k8s") {
      steps { 
        sh "kubectl get all -n monitoring"
      }
    }
    
    stage("nexus") {
      steps { 
        sh "helm package ."
        sh "curl -u test:6889388 ${NEXUS_URL} --upload-file *.tgz"
        sh "rm *.tgz"
      }
    }
    
  }
}
      

