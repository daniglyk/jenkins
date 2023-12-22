pipeline {
  agent any

  stages {
    stage("build") {
      steps {
        sh "ls"
        sh "kubectl apply -f ingress.yaml -n mediawiki"
      }
    }
  }
}
      
