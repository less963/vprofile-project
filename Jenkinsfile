pipeline {
    
	agent any
/*	
	tools {
        maven "maven3"
    }
*/	
    environment {
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "54.196.30.0:8081"
        NEXUS_REPOSITORY = "vprofile-release1"
	NEXUS_REPO_ID    = "vprofile-release1"
        NEXUS_CREDENTIAL_ID = "admin"
        ARTVERSION = "${env.BUILD_ID}"
    }
	
    stages{
        
        stage('BUILD'){
            steps {
                sh 'mvn clean install -DskipTests'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }   
        stage('UNIT TEST'){
            steps {
                sh 'mvn test'   
            }
        }
    }
}
