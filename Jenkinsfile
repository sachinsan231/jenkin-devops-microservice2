// scripted
//node {
//	stage('Build') {
//		echo "Build"
//	}
//	stage('Test') {
//		echo "Test"
//	}
//	stage('Integration Test') {
//		echo "Integration Test"
//	}
//}


// Declarative
//with declarative checkout is automated
pipeline{
	agent any
	//agent { docker { image 'node:13.8'}}
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout'){
			steps{
				//sh 'node --version'
				sh 'mvn --version'
				sh 'docker version'
				echo 'Build'
				echo "PATH - $PATH"
				echo "BUILD_URL - $env.BUILD_URL"
				/* echo 'build info'
				echo 'PATH: $PATH'
				echo 'BUILD_NUMBER : $env.BUILD_NUMBER'
				echo 'BUIL ID : $env.BUILD_ID'
				echo 'JOB NAME: $env.JOB_NAME'
				echo 'BUILD URL: $env.BUILD_URL' */
			}
		}

		stage('Compile'){
			steps{
				sh 'mvn clean compile'
			}
		}
		stage('Test'){
			steps{
				sh 'mvn test'
			}
		}
		stage('Integration Test'){
			steps{
				sh 'mvn failsafe:integration-test failsafe:verify'
			}
		} 
	} 
	post {
		always {
			echo 'Im awesome. I run always'
		}
		success {
			echo 'I run when you are successful'
		}
		failure {
			echo 'I run when you fail'
		}
	}
}