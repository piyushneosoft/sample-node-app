pipeline {
    parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: 'Git branch to build from')
        string(name: 'PORT', defaultValue: '3000', description: 'Application port')
    }
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: params.BRANCH, url: 'https://github.com/piyushneosoft/sample-node-app.git'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t node-app .' 
            }
        }
        stage('Deploy') {
            steps {
                sh "docker run -d -p ${params.PORT}:3000 sample-node-app"
            }
        }
    }
}
