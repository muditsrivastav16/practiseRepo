pipeline {
	agent { 
		node {
			label 'master'
		}
	}
	
	options {
		buildDiscarder(logRotator(numToKeepStr: '2'))
		ansiColor('xterm')
	}
	
	parameters {
		choice(name: 'ENVIRONMENT', choices: ['infra'], description: '<font color="DarkRed">There has to be only one option here</font>')
		choice(name: 'DB_MIGRATION', choices: ['updatesystem', 'none', 'initialize'], description: 'Select DB Migration')
		booleanParam(name: 'SOLR_DEPLOY', defaultValue: true, description: 'Deploy Solr')
		string(name: 'DEPLOY_BRANCH', defaultValue: 'branch', description: 'Branch Name')
		MavenMetadataParameterDefinition(name: "Maven version")
	}
	
	stages {
		stage('Build') {
			steps {
				git([url: 'https://github.com/muditsrivastav16/practiseRepo.git', branch: 'master'])
				bat 'javac CheckPipeline.java'
				bat 'java CheckPipeline'
				//sh rm -rf hybris
				//copyArtifacts(projectName: 'infra-ci-build', selector: lastSuccessful, filter: 'hybris/temp/hybris/hybrisServer/**', fingerprintArtifacts: true)                    
				//load 'hybris/temp/hybris/hybrisServer/HybrisJenkinsBuildInfo.txt'
				//load 'C:\\Jenkinsfile.txt'
			}
		}
	}
	
	//post {
	//	always {
	//		archiveArtifacts(artifacts: 'hybris/temp/hybris/hybrisServer/**', defaultExcludes: true, caseSensitive: true)
	//	}
	//}
}
