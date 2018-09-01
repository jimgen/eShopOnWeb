pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                docker-compose build
    			docker-compose up
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}