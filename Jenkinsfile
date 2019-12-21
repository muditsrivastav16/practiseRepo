pipeline {
	agent {
		node {
			label 'master'
		}
	}
	
	stages {
		stage('Build') {
			steps {
				echo 'Fetching code from github'
				git([url: 'https://github.com/muditsrivastav16/practiseRepo.git', branch: 'executingjava'])
				bat 'javac CheckPipeline.java'
				bat 'java CheckPipeline'
			}
		}
	}
}
