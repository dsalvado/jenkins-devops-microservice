pipeline {

	agent any
	//agent { docker { image 'maven:3.6.3'} }
	//agent { docker { image 'node:17.7'} }
	stages{
		stage('Build'){
			steps{
				//sh "mvn --version"
				//sh "node --version"
				echo "Build"
				echo '$PATH'
				echo " BUILD NUMBER - $env.BUILD_NUMBER"
				echo "BUILD ID - $env.BUILD_ID"
				echo "Job Name - $env.JOB_NAME"
				echo "Build Tag - $env.BUILD_TAG"
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
