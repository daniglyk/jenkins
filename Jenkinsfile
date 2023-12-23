pipeline {
  agent any

  stages {
    stage("build") {
      steps { 
        sh 'helm install ingress . -n mediawiki
      }
    }
  }
}
      
