pipeline {
  agent any

  stages {
    stage("build") {
      steps {
        sh "ls"
        sh "kubectl apply -f ingress.yaml --context cl1b58srpl7vpqdoicpj-ipic -n mediawiki"
      }
    }
  }
}
      
