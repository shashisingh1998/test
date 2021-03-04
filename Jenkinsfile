pipeline {
    agent any
    tools {
        maven 'maven'
        }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'master',
                credentialsId: 'b3622eb9-2f74-4dd7-bb43-2b487f91eee8',
                url: 'https://github.com/shashisingh1998/test.git'
                }
        }
        stage ('Clean') {
            steps {
                sh 'mvn clean'
                }
            }
	stage ('Install') {
            steps {
                sh 'mvn install'
                }
            } 
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit allowEmptyResults: true, testResults: '**/test-results/*.xml'
                }
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
