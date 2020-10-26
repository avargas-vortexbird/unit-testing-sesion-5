pipeline {
    agent any
    stages {
        stage ('Inicio') {
            
            environment {
                mvnHOME = tool 'MAVEN_HOME'
            }

            steps {

		sh  "${mvnHOME}/bin/mvn clean package -DskipTests=true"	
            }
        }

    }
}
