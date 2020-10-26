pipeline {
	agent any
	stages {
		stage ('Build Backend') {
			steps {
				def mvnHOME = tool name: "MAVEN_HOME", type: 'maven'
				sh "${mvnHOME}/bin/mvn clean package -DskipTests=true"		
			}
		}	
	}
}
