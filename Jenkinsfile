pipeline {
    agent any
    stages {
        stage ('Build Backend') {
            
            environment {
                mvnHOME = tool 'MAVEN_HOME'
            }

            steps {

		sh  "${mvnHOME}/bin/mvn clean package -DskipTests=true"	
            }
        }

	stage ('Run Test') {
            
            environment {
                mvnHOME = tool 'MAVEN_HOME'
            }

            steps {

		sh  "${mvnHOME}/bin/mvn test"	
            }
        }

	stage ('Sonar Analysts') {
            
            environment {
                scanerHome = tool 'SONAR_SCANER'
            }

            steps {
		withSonarQubeEnv('SONAR_LOCAL') {
			sh  "${scanerHome}/bin/sonar-scanner -e -Dsonar.projectKey=deployBackendCI -Dsonar.host.url=http://192.168.1.2:9000 -Dsonar.login=9ed389ae150b83b6fa99f39666b399873481facc -Dsonar.java.binaries=target -Dsonar.coverage.exclusions=**/src/test/**,**/entity/**"	
		}

            }
        }

	stage ('Quality Gate') {
            steps {
		sleep(5)
		timeout(time: 10, unit: 'MINUTES'){
			waitForQualityGate abortPipeline: true		
		}	
            }
        }


    }
}