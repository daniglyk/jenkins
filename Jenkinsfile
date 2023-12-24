pipeline {
  agent any
  triggers { pollSCM ('* * * * *')}  
  environment {
      NEXUS_URL = "https://nexus-test.belarus-devops.app/repository/helm-test/"
  }
  
  stages {
    
    stage("package") {
      steps { 
        sh '''
        sed '/0.1.0/version: 0.$env.BUILD_NUMBER.0' /test/Chart.yaml
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
      

