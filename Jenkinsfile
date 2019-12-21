pipeline {
	agent {
		node {
			label 'master'
		}
	}
	
	parameter {
		string(name: 'BUILD_BRANCH', default: 'executingjava', description: 'Branch name that will build')	
	}
	
	stages {
		stage('Build') {
			steps {
				echo 'Fetching code from github'
				bat 'hostname'
				git([url: 'https://github.com/muditsrivastav16/practiseRepo.git', branch: '${params.BUILD_BRANCH}]')
				bat 'javac CheckPipeline.java'
				bat 'java CheckPipeline'
			}
		}
	}
}
