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
		     agent any
		        steps {
			    sh 'docker build -t emdollete/spring-petclinic:latest .'
			       }
			         }
				  }
				  }
