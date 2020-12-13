node {
	
	stage('build'){
		sh './gradle clean build -x test'
	}

	stage('test'){
		sh './gradle clean test -x build'
	}

	stage('sonar'){
		 
	}

	stage('run'){
	
	}

	stage('rest'){
	
	}

	stage('nexus'){
		
	}


}