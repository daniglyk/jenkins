pipeline {
  agent any
  triggers { pollSCM ('* * * * *')}  
  
  stages {

    stage("k8s") {
      steps { 
        sh "kubectl get all -n monitoring"
      }
    }
    
    stage("nexus") {
      steps { 
        sh "helm package ."
        sh "curl -u test:6889388 https://nexus-test.belarus-devops.app/repository/helm-test/ --upload-file *.tgz"
        sh "rm *.tgz"
      }
    }
    
  }
}
      

