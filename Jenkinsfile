pipeline {
	stages {
		stage('Github') {
			steps {
				git branch: 'main', credentialsId: 'jenkins-dind', url: 'https://github.com/adawag-jef/Complete_CICD_02.git'
			}
		}
	}
}
