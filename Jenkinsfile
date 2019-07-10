#!groovy

pipeline {
 agent any
  stages {
    stage('Maven Install') {
       steps {
           sh 'mvn clean install -DskipTests'
	      }
	        }
		  stage('Docker Build') {
		  agent {label 'docker'}
		        steps {
			    sh 'docker build -f ./Dockerfile -t emdollete/spring-petclinic:latest .'
			       }
			         }
		 stage('Docker Push') {
         agent {label 'docker'}
         steps {
          withCredentials([usernamePassword(credentialsId: 'dockerhub-test', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push emdollete/spring-petclinic:latest'
				  }
				  }
}
}
}