pipeline {
  agent any
  triggers { pollSCM ('* * * * *')}  
  environment {
      NEXUS_URL = "https://nexus-test.belarus-devops.app/repository/helm-test/"
      HELM_VERSION = "version: 0.$env.BUILD_NUMBER.0"
      OLD_HELM = "version"
      DIR = "$env.BUILD_NUMBER"
  }
  
  stages {
    
    stage("package") {
      steps { 
          sh """#!/bin/bash
          sed -i 's|version: .*|${HELM_VERSION}|' ./test/Chart.yaml
          """
          sh "mv ./test ./${DIR}"
          sh "helm package ./${DIR}" 
    }
    }

    stage("deploy") {
      steps { 
        sh "helm install test ./${DIR} -n test"
      }
    }
    
    stage("nexus") {
      steps { 
        sh "curl -u $env:USER_NEXUS:$env:PASSWORD_NEXUS ${NEXUS_URL} --upload-file *.tgz"
        sh "rm *.tgz"
      }
    }
    
  }
}
      

