pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/hacker01-mika/Jenkins-ArgoCD-GitOps.git'
      }
    }
    stage('Set Remote') {
      steps {
        dir('Jenkins-ArgoCD-GitOps') {
          sh 'git config remote.origin.url https://github.com/hacker01-mika/Jenkins-ArgoCD-GitOps.git'
        }
      }
    }
  }
}
