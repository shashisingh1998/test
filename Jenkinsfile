pipeline {
    agent any
    tools {
        maven 'maven'
        }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'master',
                credentialsId: 'ab3aa4af-911e-4aa6-8cd1-9e04931f97cb',
                url: 'https://github.com/shashisingh1998/test.git'
                }
        }
        stage ('Clean') {
            steps {
                sh 'mvn clean'
                }
            }
	
        
        
	stage ('Cobertura') {
                steps {
                    sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
                    }
                }
         stage ('sonar') {
                 steps {
                   sh 'mvn sonar:sonar'
                    }
                }
	 
    }
}
