pipeline {
  agent any
  tools { 
        maven 'Maven 3.5.2'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=kevenlaziowebapp -Dsonar.organization=kevenlaziowebapp -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=5d1626fa2c9356b382705650d27af25235f40b81'
			}
    }

	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
