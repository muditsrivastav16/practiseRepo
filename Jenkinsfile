pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				batchFile 'javac CheckPiple.java'
				batchFile 'java CheckPipeline'
			}
		}
	}
}