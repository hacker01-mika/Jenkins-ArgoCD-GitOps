pipeline {
	agent any
       
	tools {
		nodejs 'NodeJS'
	}

	environment {
		DOCKER_HUB_REPO = 'michaelkakingo/cicd'
	}
	stages {
		stage('Checkout Github'){
			steps {
			    
			    git branch: 'main', credentialsId: 'GitOps-token-Github', url: 'https://github.com/hacker01-mika/Jenkins-ArgoCD-GitOps.git'
			
			}
		}		
		stage('Install node dependencies'){
			steps {
				sh 'npm install'
			}
		}
		stage('Build Docker Image'){
			steps {
				script {
					echo 'building docker iimage...'
					docker.build("${DOCKER_HUB_REPO}:latest")
					
				}
			}
		}
		stage('Trivy Scan'){
			steps {
				sh '''
				 echo 'scan docker with trivy '
				'''

			}
		}
		stage('Push Image to DockerHub'){
			steps {
				script {
					echo 'pushing docker image to DockerHub...'
					}
				}
			}
		stage('Install Kubectl & ArgoCD CLI'){
			steps {
				sh '''
				echo 'installing Kubectl & ArgoCD cli...'
				'''
			}
		}
		stage('Apply Kubernetes Manifests & Sync App with ArgoCD'){
			steps {
				script {
    						sh '''
							echo 'synchronizing app with ArgoCD'
						'''
					}	
				}		
		}
	}

	post {
		success {
			echo 'Build & Deploy completed succesfully!'
		}
		failure {
			echo 'Build & Deploy failed. Check logs.'
		}
	}
}

