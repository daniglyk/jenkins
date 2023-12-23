pipeline {
  agent any

  stages {
    stage("build") {
      steps { 
        sh 'kubectl apply -f ingress.yaml -n mediawiki'
      }
    }
  }
}
      
