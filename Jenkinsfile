pipeline {
    agent any
	 parameters {
        booleanParam(name: "RUN_INTEGRATION_TESTS ", defaultValue: true)
    }
    stages { 
        stage('Install Dependencies) {
            steps { sh './mvnw clean install' }
        }
        stage('Test') {
            parallel { 
                stage('Unit tests') {
                    steps { sh './mvnw test -D testGroups=unit' }
                }
                stage('Integration tests') {
                    steps { sh './mvnw test -D testGroups=integration' }
                }
            }
        }
    }
}
