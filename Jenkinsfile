// SCRIPTED approach

// node {
// 	echo "Build"
// 	echo "Test"
// 	echo "Integration Test"
// }

// DECLARATIVE approach
pipeline {
	agent any
	// agent	{ docker { image 'maven:3.6.3'} }	
	// agent	{ docker { image 'node:24.1'} }	
	environment {
		dockerHome = tool 'myDocker' 
		mavenHome = tool 'myMaven' 
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage ('Build') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env."
				echo "BUILD_ID - $env.BUILD_ID"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage ('Test') {
			steps {
				echo "Test"
			}
		}
		stage ('Integration Test') {
			steps {
				echo "Integration Test"
			}
		}
	} 	
	post {
		always {
			echo 'Im awsome. I run always'
		}
		success {
			echo 'I run when you are successful'
		}
		failure {
			echo 'I run when you fail'
		}
	}
}