pipeline {
	agent {
		node {
			label 'master'
		}
	}
	
	parameters {
		string(name: 'BUILD_BRANCH', defaultValue: 'executingjava', description: 'Branch name that will build')	
	}
	
	stages {
		stage('Build') {
			steps {
				echo 'Fetching code from github'
				bat 'hostname'
				git([url: 'https://github.com/muditsrivastav16/practiseRepo.git', branch: "${params.BUILD_BRANCH}"])
				bat 'javac CheckPipeline.java'
				bat 'java CheckPipeline'
				
				withPythonEnv('CPython-3.5.2') {
					sh 'echo Hello'
				}
			}
		}
	}
}
