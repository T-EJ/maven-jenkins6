pipeline {
    agent any
    stages {
        stage('git-code-download') {
            steps {
                echo "Download code from Git"
                git branch: 'main', url: 'https://github.com/T-EJ/maven-jenkins6.git'
            }
        }
        stage('create-docker-image') {
            steps {
                sh '''
                docker build -t devopstechlab/javawebapp:${BUILD_NUMBER} .
                docker tag devopstechlab/javawebapp:${BUILD_NUMBER} devopstechlab/javawebapp:latest
                '''
            }
        }
    }
}
