node {
	
	stage('build'){
		bat 'dir'
		bat 'gradle clean build -x test'
	}

	stage('test'){
		bat 'gradle clean test -x build'
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