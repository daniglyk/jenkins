pipeline {
  agent any
  triggers { pollSCM ('* * * * *')}  
  environment {
      NEXUS_URL = "https://nexus-test.belarus-devops.app/repository/helm-test/"
  }
  
  stages {
    
    stage("package") {
      steps { 
        sh "helm package ./test"
      }
    }

    stage("deploy") {
      steps { 
        sh "helm upgade test ./test -n test"
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
      

