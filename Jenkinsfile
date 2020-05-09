pipeline {
	agent any
	stages {

		stage('Lint HTML') {
			steps {
				sh 'tidy -q -e *.html'
			}
		}

		stage('Building image') {
			steps {
				echo 'Building Docker image...'
				sh "cat ~/my_password.txt | docker login --username mayman93 --password-stdin"
				sh "docker build --tag=mayman93/capstone ."
				sh "docker push mayman93/capstone"
			}
			
		}

		stage('Deploy to AWS EKS') {
			steps {
				sh "aws eks --region eu-west-2 update-kubeconfig --name capstone"
				sh "kubectl run capstone  --image=jenkins.dkr.ecr.us-west-2.amazonaws.com/capstone:latest"
			}
		}
	}
}
