pipeline {

	agent any
	//agent { docker { image 'maven:3.6.3'} }
	//agent { docker { image 'node:17.7'} }

	environment {
		dockerHome = tool 'myDocker'
		manvenHome = tool 'myMaven'

		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages{
		stage('Checkout'){
			steps{
				sh "mvn --version"
				sh "docker --version"
				echo "Build"
				echo "Path is -> $PATH"
				echo " BUILD NUMBER - $env.BUILD_NUMBER"
				echo "BUILD ID - $env.BUILD_ID"
				echo "Job Name - $env.JOB_NAME"
				echo "Build Tag - $env.BUILD_TAG"
				echo "PATH -> $PATH "
			}
		}
		stage('Complile'){
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				sh "mvn test"
			}
		}
		stage('Integration Test'){
			steps{
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage('Package'){
			steps{
				sh "mvn package -DskipTest"
			}
		}
		stage('Build Docker Image'){
			steps{
				//"docker build -t dsalvado/currency-exchange-devops:$env.BUILD_TAG"
				script{
					dockerImage = docker.build("dsalvado/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push Docker Image'){
			steps{
				script{
					docker.withRegistry('','dockerhub'){
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
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
