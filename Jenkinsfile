pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-hub-credentials')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t rakshit/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
                sh 'docker tag nodeapp rakshit/nodeapp'
				sh 'docker image push rakshit/nodeapp:latest'
			}
		}
	}

	

}