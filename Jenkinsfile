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
		NAME = "HYBRIS"
		//DESCRIPTION = "Choose Hybris Release"
		REPOSITORYBASEURL = "http://repo.y.balsamhill.com:8081/nexus/content/repositories/release"
		REPOSITORYCREDENTIALS = "nexusdeployer"
		ARTIFACTGROUPID = "com.balsam"
		ARTIFACTID = "hybris_platform"
		PACKAGING = "zip"
		DEFAULTVALUE = "LATEST"
		SORTINGORDER = "DESC"
	}
	
	stages {
		stage('Build') {
			steps {
				git([url: 'https://github.com/muditsrivastav16/practiseRepo.git', branch: "${params.DEPLOY_BRANCH}"])

				script {
					userInput = input(
						id: "userInput",
						message: "choose jar version",
						parameters: [[
							$class: "MavenMetadataParameterDefinition",
							name: "${NAME}",
							description: "choose hybris release", //"${DESCRIPRION}",
							repoBaseUrl: "${REPOSITORYBASEURL}",
							groupId: "${ARTIFACTGROUPID}",
							artifactId: "${ARTIFACTID}",
							packaging: "${PACKAGING}",
							defaultValue: "${DEFAULTVALUE}",
							classifier: "",
							versionFilter: "",
							sortOrder: "${SORTINGORDER}",
							maxVersions: "",
							currentArtifactInfoUrl: "",
							currentArtifactInfoLabel: "",
							currentArtifactInfoPattern: "",
							credentialId: "${REPOSITORYCREDENTIALS}"
							]],
						)
					print(userInput)
				}


				echo "${NAME}"
				echo "${DESCRIPRION}"
				echo "${REPOSITORYBASEURL}"
				echo "${REPOSITORYCREDENTIALS}"
				echo "${ARTIFACTGROUPID}"
				echo "${ARTIFACTID}"
				echo "${PACKAGING}"
				echo "${DEFAULTVALUE}"
				echo "${SORTINGORDER}"


				bat 'sh ShellScript.sh'
				

				
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