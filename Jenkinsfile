pipeline {
	agent { 
		node {
			label 'master'
		}
	}
	
	options {
		buildDiscarder(logRotator(numToKeepStr: '2'))
	}
	
	parameters {
		choice(name: 'ENVIRONMENT', choices: ['infra'], description 'There has to be only one option here')
		choice(name: 'DB_MIGRATION', choices: ['updatesystem', 'none', 'initialize'])
		booleanParam(name: 'SOLR_DEPLOY', defaultValue: true, description: 'Deploy Solr')
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
