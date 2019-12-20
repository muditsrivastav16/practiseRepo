pipeline {
	agent { 
		node {
			label 'master'
			currentBuild.description = 'This is the Description'
		}
	}
	stages {
		stage('Build') {
			steps {
				git([url: 'https://github.com/muditsrivastav16/practiseRepo.git', branch: 'master'])
				bat 'javac CheckPipeline.java'
				bat 'java CheckPipeline'
			}
		}
	}
}
