pipeline {
	agent { 
		node {
			label 'master'
		}
	}
	stages {
		stage('Build') {
			steps {
				git([url: 'https://github.com/muditsrivastav16/practiseRepo.git', branch: 'master'])
				bat 'javac CheckPipeline.java'
			}
		}
	}
}
