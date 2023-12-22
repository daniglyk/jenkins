pipeline {
  agent any

  stages {
    stage("build") {
      steps {
        sh "ls"
        sh "kubectl apply -f ingress.yaml --context test -n mediawiki"
      }
    }
  }
}
      
