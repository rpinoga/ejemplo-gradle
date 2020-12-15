pipeline {
    agent any

    stages {
        stage('Pipeline') {
        	steps{
	        	script{
	        		stage('build & test'){
	        			sh './gradlew clean build'
	        			//bat 'gradlew clean build'
	        		}
	        		stage('sonar'){
						def scannerHome = tool 'sonar';
						withSonarQubeEnv('sonar') {
							sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=ejemplo-gradle -Dsonar.java.binaries=build"
							//bat "${sonarhome}\\bin\\sonar-scanner -Dsonar.projectKey=ejemplo-gradle -Dsonar.java.binaries=build"
						}
	        		}
	        		stage('run'){
	        			sh 'nohup bash gradlew bootRun &'
	        			//bat "nohup start gradlew bootRun &"
	        		}
	        		stage('rest'){
	        			sh  "curl -X GET http://localhost:8082/rest/mscovid/test?msg=testing"
	        			//bat "curl -X GET http://localhost:8082/rest/mscovid/test?msg=testing"
	        		}
	        		stage('nexus'){
	        			nexusPublisher nexusInstanceId: 'nexus', nexusRepositoryId: 'test-nexus', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: 'jar', filePath: 'build/libs/DevOpsUsach2020-0.0.1.jar']], mavenCoordinate: [artifactId: 'DevOpsUsach2020', groupId: 'com.devopsusach2020', packaging: 'jar', version: '0.0.1']]]
	        		}
	        	}
        	}
        }
    }
}
