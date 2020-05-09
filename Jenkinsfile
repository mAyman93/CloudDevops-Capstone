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
				sh "docker login -u mayman93 -p ${env.dockerPassword}"
				sh "docker build -t ${env.dockerUsername}/capstone ."
				sh "docker tag capstone ${env.dockerUsername}/capstone"
				sh "docker push ${env.dockerUsername}/capstone"
			}
			
		}
	}
}
