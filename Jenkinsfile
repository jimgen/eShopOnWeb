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
    		steps {
        		script {
          		// requires SonarQube Scanner 2.8+
          		scannerHome = tool 'SonarQube Scanner 2.8'
        		}
        		withSonarQubeEnv('SonarQube Scanner') {
          			sh "${scannerHome}/bin/sonar-scanner"
        		}
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