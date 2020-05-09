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
				sh "docker login -u mayman93 -p Mm.123123"
				sh "docker build -t mayman93/capstone ."
				sh "docker tag capstone mayman93/capstone"
				sh "docker push mayman93/capstone"
			}
			
		}
	}
}
