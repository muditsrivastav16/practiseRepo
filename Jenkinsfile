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
		string(name: 'DEPLOY_BRANCH', defaultValue: 'practise', description: 'Branch Name')
	}

	environment {
		MYNAME = 'Mudit'
		MVNARTIFACTS = get_MVN_Artifacts()
	}
	
	stages {
		stage('Build') {
			steps {
				git([url: 'https://github.com/muditsrivastav16/practiseRepo.git', branch: "${params.DEPLOY_BRANCH}"])
				bat 'sh ShellScript.sh'
				bat 'javac CheckPipeline.java'
				bat 'java CheckPipeline !'
				echo "${userInput}"
				echo "${myname}"
				echo "${env.myname}"

				
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
def get_MVN_Artifacts() {
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
	return ("${userInput}")
}