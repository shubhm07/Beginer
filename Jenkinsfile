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
		      sh 'gradle --stop'
		      sh 'gradle --status'
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
