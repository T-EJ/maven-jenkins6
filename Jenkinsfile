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
                docker build -t tejmt/javawebapp:${BUILD_NUMBER} .
                docker tag tejmt/javawebapp:${BUILD_NUMBER} tejmt/javawebapp:latest
                docker push tejmt/javawebapp:${BUILD_NUMBER}
                docker push tejmt/javawebapp:latest
                '''
            }
        }
    }
}
