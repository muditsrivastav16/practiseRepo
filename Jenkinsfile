pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				git([url: 'https://github.com/muditsrivastav16/practiseRepo.git', branch: 'master'])
				sh 'javac CheckPipeline.java'
				sh 'java CheckPipeline'
			}
		}
	}
}
