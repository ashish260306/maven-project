pipeline {
  agent any 
	properties([parameters([string(defaultValue: 'staging', description: 'deploy to staging', name: 'qa', trim: false)])])
	
	triggers {
	   pollSCM('* * * * *')
	}
	
     stages{
        stage('Build'){
          steps {
              sh 'mvn clean package'
           }
                   post {
                      success {
                              echo 'Now Archiving...'
                                  archiveArtifacts artifacts: '**/target/*.war'
                                }
                        }
        }
		stage('Deploy') {
		   steps {
		      echo "Deploy to staging"
			}
		}
	}
}
