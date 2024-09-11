pipeline {
  agent any
  stages {
    stage('git pull') {
      steps {
        // https://github.com/wja30/GitOps.git will replace by sed command before RUN
        git url: 'https://github.com/wja30/GitOps.git', branch: 'master'
      }
    }
    stage('Apply Kubernetes files') {
    withKubeConfig([credentialsId: 'kubeconfig', serverUrl: 'https://192.168.56.30']) {
      sh 'kubectl apply -f deployment.yaml'
    }
  }
}
}
