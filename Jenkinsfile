pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'dotnet build'
    			sh 'dotnet restore'
            }
        }
        stage('SonarQube analysis') {
    	def scannerHome = tool 'SonarQube Scanner 2.8';
    		withSonarQubeEnv('My SonarQube Server') {
      			sh "${scannerHome}/bin/sonar-scanner"
    		}
  		}
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'dotnet test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}