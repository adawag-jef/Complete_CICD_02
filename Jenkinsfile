pipeline {
	agent any
	tools {
		nodejs 'NodeJS'
		
	}
	environment {
		SONAR_PROJECT_KEY = 'complete-cicd'
		SONAR_SCANNER_HOME = tool 'SonarQubeScanner'
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
		stage('SonarQube Analysis') {
			steps {
				withCredentials([string(credentialsId: 'complete-cicd-token', variable: 'SONAR_TOKEN')]) {
				   	withSonarQubeEnv('SonarQube') {
						sh """
	 					${SONAR_SCANNER_HOME}/bin/sonar-scanner \
       						-Dsonar.projectKey=${SONAR_PROJECT_KEY} \
	     					-Dsonar.sources=. \
	   					-Dsonar.host.url=http://54.251.28.57:9000 \
	 					-Dsonar.login=${SONAR_TOKEN}
       						"""
					}
				}
			}
		}
	}
}
