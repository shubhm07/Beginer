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
		withSonarQubeEnv(installationName: 'SonarQubeScanner', credentialsId: 'sonar-token') {
		      sh 'chmod +x gradlew'
		      sh "./gradlew sonarqube \
                          -Dsonar.projectKey=${serviceName} \
                  	  -Dsonar.host.url=${env.SONAR_HOST_URL} \
                  	  -Dsonar.login=${env.SONAR_AUTH_TOKEN} \
                  	  -Dsonar.projectName=${serviceName} \
                  	  -Dsonar.projectVersion=${BUILD_NUMBER}"
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
