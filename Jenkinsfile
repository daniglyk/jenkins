pipeline {
  agent any
  triggers { pollSCM ('* * * * *')}  
  environment {
      NEXUS_URL = "https://nexus-test.belarus-devops.app/repository/helm-test/"
      HELM_VERSION = "version: 0.$env.BUILD_NUMBER.0"
  }
  
  stages {
    
    stage("package") {
      steps { 
        sh '''
        sed -i "/version/${HELM_VERSION}" /test/Chart.yaml
        helm package ./test
        '''
      }
    }

    stage("deploy") {
      steps { 
        sh "helm install test ./test -n test"
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
      

