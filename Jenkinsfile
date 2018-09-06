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
            	sh "docker run -ti -v $(pwd):/root/src --link sonarqube newtmitch/sonar-scanner sonar-scanner \
  					-Dsonar.host.url=http://sonarqube:9000 \
  					-Dsonar.jdbc.url=jdbc:h2:tcp://sonarqube/sonar \
  					-Dsonar.projectKey=${env.JOB_NAME} \
  					-Dsonar.projectName="${env.JOB_NAME}" \
  					-Dsonar.projectVersion=1 \
  					-Dsonar.projectBaseDir=/root \
  					-Dsonar.sources=./src"
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