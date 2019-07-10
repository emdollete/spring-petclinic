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
				  }
				  }
