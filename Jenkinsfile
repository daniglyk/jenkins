pipeline {
  agent any

  stages {
    stage("build") {
      steps { 
        sh "export KUBECONFIG=~/.kube/config"
        sh "helm install ingress . -n mediawiki"
      }
    }
  }
}
      
