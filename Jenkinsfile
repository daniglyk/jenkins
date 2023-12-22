pipeline {
  agent any

  stages {
    stage("build") {
      steps {
        sh "ls"
        kubectl apply -f ingress.yaml -n mediawiki
      }
    }
  }
}
      
