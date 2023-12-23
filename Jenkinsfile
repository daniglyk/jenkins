pipeline {
  agent any

  stages {
    stage("build") {
      steps {
        sh 'curl -LO "https://storage.googleapis.com/kubernetes-release/release/v1.20.5/bin/linux/amd64/kubectl"'  
        sh 'chmod u+x ./kubectl'  
        sh '/usr/local/bin/kubectl apply -f ingress.yaml -n mediawiki'
      }
    }
  }
}
      
