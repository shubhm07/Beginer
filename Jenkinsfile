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
		withSonarQubeEnv(credentialsId: 'sonar-token') {
		      sh 'chmod +x gradlew'
		      sh './gradlew sonarqube --warning-mode all'
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
