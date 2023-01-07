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
	stages{
		stage('Build'){
			steps{
				echo 'Build'
			}
		}
		stage('Test'){
			steps{
				echo 'Test'
			}
		}
		stage('Integration Test'){
			steps{
				echo 'Integration Test'
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