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
				withCredentials([usernamePassword(credentialsId: 'dockerhub-test', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
				sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
			    sh 'docker build -f ./Dockerfile -t emdollete/spring-petclinic:latest .'
				sh 'docker run -p 8081:8080 emdollete/spring-petclinic'
				sh 'docker push emdollete/spring-petclinic:latest'
				}
			       }
			         }
}
}
