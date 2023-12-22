pipeline {
  agent any

  stages {
    stage("build") {
      steps {
        sh "ls"
        sh "kubectl apply -f ingress.yaml --context catt5ri72eeochn7oaib -n mediawiki"
      }
    }
  }
}
      
