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
			    sh 'docker build -t emdollete/spring-petclinic:latest -f ./Dockerfile'
			       }
			         }
				  }
				  }
