pipeline {
 agent {
 node {
 label 'cl1b58srpl7vpqdoicpj-ipic' //set your kubernetes node
 }
}

 stages {
 stage('Preparation') {
 steps {
 cleanWs()
 git credentialsId: '4f89e728-31ef-4ab3-a781-3e1d9b4ce504', url: "https://github.com/daniglyk/jenkins.git"
 }
 }
 stage('Build') {
 steps {
 sh 'echo No build required for Gateway'
 }
 }

 stage('configFileProvider') {
 steps { 
 configFileProvider([configFile(fileId: '1e2d0069-824a-449e-9a3f-9dc704404dad', targetLocation: '/home/root2/jenkins/workspace/workspace/test2'), configFile(fileId: '641db19b-5692-4ada-ac39-da4a996a8ab9', targetLocation: '/home/root2/jenkins/workspace/workspace/test2')]) {
// some block
 }
 } 
 }


 stage('Deploy to Cluster') {
 steps {
 helm install mediawiki . -n wikimedia
 }
 }
 }
}
