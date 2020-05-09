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
				withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
						sh "docker login -u ${env.dockerUsername} -p ${env.dockerPassword}"
						sh "docker build -t ${registry} ."
						sh "docker tag capstone ${env.dockerUsername}/capstone"
						sh "docker push ${env.dockerUsername}/capstone"
				}
			}
			
		}
	}
}
