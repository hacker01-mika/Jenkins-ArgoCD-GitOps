pipeline {
	agent any

	stages {
		stage('Checkout Github'){
			steps {
			    sh '''
			    echo 'Checking out code'
				'''
			}
		}		
		stage('Install node dependencies'){
			steps {
				sh '''
				echo 'installing node dependencies'
				'''
			}
		}
		stage('Build Docker Image'){
			steps {
				script {
					echo 'building docker image...'
					
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

