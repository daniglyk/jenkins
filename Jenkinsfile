pipeline {
  agent any

  stages {
    stage("build") {
      steps {
        sh "apt-get update"  
        sh 'apt-get install kubectl'  
        sh 'kubectl apply -f ingress.yaml -n mediawiki'
      }
    }
  }
}
      
