#!groovy
#pipeline {
#    agent none
#   stages {     
#    stage('Maven Install') {
#      agent {         
#       docker {          
#         image 'maven:3.5-jdk-8'         
#      }       
#   }       
#   steps {
#	sh 'mvn clean install'
#	 }
#      }
# }
#}
node 'docker' {
   stage ('Maven Install') {
   	sh 'mvn clean install'
   }
}
