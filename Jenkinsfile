pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				git([url: 'https://github.com/muditsrivastav16/practiseRepo.git', branch: 'master'])
				bat label: '', script: '''javac CheckPipeline.java'''
				bat label: '', script: '''java CheckPipeline'''
			}
		}
	}
}
