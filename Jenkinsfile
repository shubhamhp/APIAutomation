pipeline{
	agent any
	
	stages{
		stage("Checkout code"){	
		steps{
			checkout scm
		}
		}

		stage("Run Postman Suite"){
		steps{
			echo "Installing newman and html reporter"
			bat "npm install -g newman newman-reporter-htmlextra"

			echo "Executing the framework for 50 users"
			bat "newman run Runner_Practice.postman_collection.json -e New Environment.postman_environment.json -d test_data.csv -r cli,htmlextra" 
			}
		}
	}
	post {
        always {
            echo "Archiving Newman HTML Report..."
            archiveArtifacts artifacts: 'newman/*.html', allowEmptyArchive: true
        }
    }
}