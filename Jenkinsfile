#!groovy

pipeline {
 agent any
  stages {
    stage('Maven Install') {
       steps {
           sh 'mvn clean install -DskipTests'
	      }
	        }
		  stage('Docker Build and Push') {
		  agent {label 'docker'}
		        steps {
				withCredentials([usernamePassword(credentialsId: '528129de-2b5d-4d30-9dc6-17a963f1b9fd', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
				sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
			        sh 'docker build -f ./Dockerfile -t calclabacr.azurecr.io/spring-petclinic:latest .'
				sh 'docker push calclabacr.azurecr.io/spring-petclinic:latest'
				}
			       }
			         }
}
}
