pipeline {

	//agent any
	//agent { docker { image 'maven:3.6.3'} }
	agent { docker { image 'node:17.7'} }
	stages{
		stage('Build'){
			steps{
				//sh "mvn --version"
				sh "node --version"
				echo "Build"
			}
		}
		stage('Test'){
			steps{
				echo "Test"
			}
		}
		stage('Integration Test'){
			steps{
				echo "Integration Test"
			}
		}
	} 
	post {
		always{
			echo "I always run."
		}
		success {
			echo 'I run when successful'
		}
		failure {
			echo 'I run when there is a failure'
		}

	}

}
