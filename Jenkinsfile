pipeline {

	agent any
	tools {
		maven 'm360'
	}

	stages {
	  stage('build') {
		steps {
		  bat 'mvn install -DskipTests'
		}
	  }

	  stage('test') {
		steps {
		  bat 'mvn test'
		  
		  post {
				archiveArtifacts artifacts: 'target/**.jar', followSymlinks: false
				junit stdioRetention: '', testResults: 'target/surefire-reports/*.xml'
			}
		}
	  }

}

}
