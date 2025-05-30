// SCRIPTED approach

// node {
// 	echo "Build"
// 	echo "Test"
// 	echo "Integration Test"
// }

// DECLARATIVE approach
pipeline {
	agent any
	stages {
		stage ('Build') {
			steps {
				echo "Build"
				// echo "Test"  # V1 : All 'steps' in 1 'stage'
				// echo "Integration Test"
			}
		}
		// V2: add stages : 
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