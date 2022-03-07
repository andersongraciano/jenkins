pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('bernardo9999')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t bernardo9999/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push bernardo9999/nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
