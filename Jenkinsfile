pipeline {
  agent any 
  environment {
      NEXUS_URL = "https://nexus-test.belarus-devops.app/repository/helm-test/"
      HELM_VERSION = "version: 0.$env.BUILD_NUMBER.0"
  }
  
  stages {
    
    stage("package") {
      steps { 
          sh """#!/bin/bash
          sed -i 's|version: .*|${HELM_VERSION}|' ./test/Chart.yaml
          """
          sh "helm package ./test" 
    }
    }

    stage("deploy") {
      steps { 
        sh "helm upgrade test ./test -n test"
      }
    }
    
    stage("nexus") {
      steps { 
        sh "curl -u test:6889388 ${NEXUS_URL} --upload-file *.tgz"
        sh "rm *.tgz"
      }
    }
    
  }
}
      

