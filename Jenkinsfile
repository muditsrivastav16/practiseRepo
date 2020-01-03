pipeline {
	agent { 
		node {
			label 'master'
		}
	}

	environment {
		envVariable = 'envValue'
	}
	
	options {
		buildDiscarder(logRotator(numToKeepStr: '2'))
		ansiColor('xterm')
	}
	
	parameters {
		string(name: 'DEPLOY_BRANCH', defaultValue: 'practise', description: 'Branch Name')
	}
	
	stages {
		stage('Input') {
			steps {

				script {
					userInput = input(
						id: "userInput",
						message: "choose jar version",
						parameters: [[
							$class: "MavenMetadataParameterDefinition",
							name: "version",
							description: "List Maven Artifacts Versions",
							repoBaseUrl: "",
							groupId: "",
							artifactId: "",
							packaging: "",
							defaultValue: "",
							classifier: "",
							versionFilter: "",
							sortOrder: "DESC",
							maxVersions: "",
							currentArtifactInfoUrl: "",
							currentArtifactInfoLabel: "",
							currentArtifactInfoPattern: "",
							credentialId: ""
						]],
					)
					print(userInput)
				}
			}
		}

		stage('Build') {
			steps {
				git([url: 'https://github.com/muditsrivastav16/practiseRepo.git', branch: "${params.DEPLOY_BRANCH}"])
				bat 'sh ShellScript.sh'
				bat 'javac CheckPipeline.java'
				bat 'java CheckPipeline !'
				echo "${userInput}"

				
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
