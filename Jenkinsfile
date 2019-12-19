pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				git([url: 'https://github.com/muditsrivastav16/practiseRepo.git', branch: 'master'])
				batchFile javac CheckPipeline.java
				batchFile java CheckPipeline
			}
		}
	}
}
