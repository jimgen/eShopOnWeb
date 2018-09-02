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
        	agent {
                docker { image 'newtmitch/sonar-scanner:latest' }
            }
    		steps {
            	sh "sonar-scanner"
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