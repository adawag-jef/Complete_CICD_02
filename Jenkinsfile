pipeline {
	agent any
	tools {
		nodejs 'NodeJS'
		
	}
	environment {
		SONAR_PROJECT_KEY = 'complete-cicd'
		SONAR_SCANNER_HOME = tool 'SonarQubeScanner'
		DOCKER_HUB_REPO = 'jefadawag/complete-cicd'
	}
	stages {
		stage('Github') {
			steps {
				git branch: 'main', credentialsId: 'jenkins-dind', url: 'https://github.com/adawag-jef/Complete_CICD_02.git'
			}
		}
		stage('Unit Test') {
			steps {
				sh 'npm install'
				sh 'npm test'
			}
		}

		stage('Docker Image') {
			steps {
				script {
					docker.build("${DOCKER_HUB_REPO}:latest")
				}
			}
		}
	}
}
