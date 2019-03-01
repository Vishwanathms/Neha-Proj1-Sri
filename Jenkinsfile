pipeline {
agent any
tools {
       
        maven 'maven3'
	
 }
stages {
	stage('build') {
            steps {
		        configFileProvider([configFile(fileId: 'config', variable: 'MAVEN_SETTINGS_XML')]) {
                       git branch: 'develop', credentialsId: 'github', url: 'https://github.com/nehasai/sampleapi.git'
		      sh "mvn -s $MAVEN_SETTINGS_XML clean test -DskipTests"
			}
	    }
   }
	stage('MUnit Test Report') {
		steps {
                script {
              publishHTML(target:[allowMissing: false,alwaysLinkToLastBuild: true,keepAll: true,reportDir: 'target/site/munit/coverage',reportFiles: 'summary.html',reportName: 'MUnit Test Report',reportTitles: 'MUnit Test Coverage Report'])
              }
              }
}
}
}

    
 

