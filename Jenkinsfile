node {
	
	checkout scm
	
	stage('build'){
		bat 'dir'
		bat 'gradle clean build -x test'
	}

	stage('test'){
		bat 'gradle clean test -x build'
	}

	stage('sonar'){
        withSonarQubeEnv(installationName: 'sonar') {
            sh 'gradle sonarqube'
        }
	}

	stage('run'){
	
	}

	stage('rest'){
	
	}

	stage('nexus'){
		
	}


}