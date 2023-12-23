pipeline {
  agent any

  stages {
    stage("build") {
      steps { 
        sh "curl -sSL https://storage.yandexcloud.net/yandexcloud-yc/install.sh | bash"
        sh 'source "/home/jenkins/.bashrc"'
        sh "kubectl get pods -n monitoring"
      }
    }
  }
}
      
