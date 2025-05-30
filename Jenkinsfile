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
		JAVA_HOME = tool 'myJdk'
		PATH = "$dockerHome/bin:$mavenHome/bin:$JAVA_HOME/bin:$PATH"
	}
	stages {
		stage ('Checkout') {
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
		stage ('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}
		stage ('Test') {
			steps {
				sh "mvn test"
			}
		}
		stage ('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
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