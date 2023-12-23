pipeline {
  agent any

  stages {
    stage("build") {
      steps {
        sh "sudo apt-get update"  
        sh 'sudo apt-get install kubectl'  
        sh 'kubectl apply -f ingress.yaml -n mediawiki'
      }
    }
  }
}
      
