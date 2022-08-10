pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('ahmed-dockerhub-token')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t nxzcint/game:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push nxzcint/game:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
