pipeline {

  agent any
  stages {
    stage('Checkout Code'){
      steps {
        node('master') {
          deleteDir()
          checkout scm
          stash 'code'
        }
      }
    }	   
		stage('Build App package') {
			steps{
				 
				sh 'cd /var/lib/jenkins/workspace/Webapp_Azure/complete/ && sudo mvn package'
				
				  
			    }
		}

		stage('Create Docker image and publish to Azure') {
			steps{
			
				azureWebAppPublish appName: 'Mywebapp18', azureCredentialsId: '9aec816d-964e-4525-b961-2c3817000b33', dockerFilePath: 'complete/Dockerfile', dockerImageName: '', dockerImageTag: '', dockerRegistryEndpoint: [credentialsId: 'dc424f42-fb84-4a6e-9ae5-43ad3415a0ad', url: 'https://jenkinsregistry18.azurecr.io'], filePath: '', publishType: 'docker', resourceGroup: 'myResourceGroup', slotName: '', sourceDirectory: '', targetDirectory: ''
				
				}
			}	


}
