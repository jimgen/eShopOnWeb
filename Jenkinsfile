pipeline {
    agent {
        docker { image 'microsoft/dotnet' }
    }
    stages {
        stage('Build') {

            steps {
                echo 'Building..'
                sh 'dotnet publish'
    			sh 'dotnet restore'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh "pwd"
            	sh "ls"
                sh "dotnet test ./tests/UnitTests/UnitTests.csproj /p:CollectCoverage=true /p:CoverletOutputFormat=json"
            }
        }
        stage('SonarQube analysis') {
    		steps {
            	sh "sonar-scanner -Dsonar.host.url=http://localhost:9000 -Dsonar.projectKey=eShopOnWeb -Dsonar.projectVersion=1 -Dsonar.projectBaseDir=. -Dsonar.sources=./src"	
        	}
  		}
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}