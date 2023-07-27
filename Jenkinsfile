

// def COLOR_MAP = [
//	'SUCCESS' : 'good',
//	'FAILURE' : 'danger',
//]

pipeline {
	agent any
	tools {
		maven "MAVEN3"
		jdk "OracleJDK8"
	}
	environment {
		SNAP_REPO = 'vprofile-snapshot'
		NEXUS_USER = 'admin'
		NEXUS_PASS = 'admin@123'
		RELEASE_REPO = 'vprofile-release'
		CENTRAL_REPO = 'vpro-maven-central'
		NEXUSIP = '172.31.6.68'
		NEXUSPORT = '8081'
		NEXUS_GRP_REPO = 'vprofile-maven-group'
		NEXUS_LOGIN = 'nexuslogin'
		SONARSERVER = 'sonarserver'
  	        SONARSCANNER = 'sonarscanner'
	}
	stages {
		stage ('Build') {
			steps { 
				sh 'mvn -s settings.xml  -DskipTests install'

			}
			post {
				success {
					echo "Now Archiving."
					archiveArtifacts artifacts : '**/*.war'
				}
		       }  

		}
		stage ('Test') {
			steps {
				sh 'mvn -s settings.xml test'
			}
		}
		stage ('Checkstyle Analysis') {
			steps {
				sh 'mvn -s settings.xml checkstyle:checkstyle'
			}
		}
		stage ('Sonar Analysis') {
			environment  {
				scannerHome =tool "${SONARSCANNER}"
			}
			steps {
				withSonarQubeEnv("${SONARSERVER}")
				{
				sh '''${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=vprofile \
                   		-Dsonar.projectName=vprofile-repo \
                   		-Dsonar.projectVersion=1.0 \
                   		-Dsonar.sources=src/ \
                   		-Dsonar.java.binaries=target/test-classes/com/visualpathit/account/controllerTest/ \
                   		-Dsonar.junit.reportsPath=target/surefire-reports/ \
                   		-Dsonar.jacoco.reportsPath=target/jacoco.exec \
                   		-Dsonar.java.checkstyle.reportPaths=target/checkstyle-result.xml''' 
				}
			}
		}
		stage ('Quality Gate') {
			steps {
				timeout (time : 5, unit : 'HOURS') {
					waitForQualityGate abortPipeline :true
				}
			}
		}
		stage ('Upload Artifact') {
			steps { 
				nexusArtifactUploader (
					nexusVersion : 'nexus3',
					protocol : 'http',
					nexusUrl : "${NEXUSIP}:${NEXUSPORT}",
					groupId : "QA",
					version : "${env.BUILD_ID}-${env.BUILD_TIMESTAMP}",
					repository : "${RELEASE_REPO}",
					credentialsId : "${NEXUS_LOGIN}",
					artifacts : [
						[
							artifactId : 'vproapp',
							classifier : '',
							file : 'target/vprofile-v2.war',
							type : 'war'
							
						]
					]
					
				)
			}
		}
	}
	post{
		always {
			echo 'slack notification'
			slackSend channel : '#cicd-1',
				color : COLOR_MAP[currentBuild.currentResult],
					message : "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} \n More Infor at : ${env.BUILD_URL}"
		
		}
	}

}
