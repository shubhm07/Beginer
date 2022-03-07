pipeline{
    agent any
    stages{
	stage("Sonar Quality Check"){
	    agent{
	       docker {
		    image 'openjdk:11'
	       }
	    }
	    steps{
	       echo "============ Executing Sonar Quality Check ============"
	       script{
		withSonarQubeEnv(credentialsId: 'sonar-token1') {
		      sh './gradlew --stop'
		      sh './gradlew --status'
		      sh './gradlew --daemon'
		      sh './gradlew --warning-mode all'
		      sh './gradlew --scan'
		      sh 'chmod +x gradlew'
		      sh './gradlew sonarqube'
		    }
		}
	    }
	}
    }
	post{
	     always{
		 echo " Success "
	     }
	}
}
