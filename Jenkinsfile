pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/samvitkar7150/java-docker-jenkins-maven.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t java-app:1.0 .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop java-app || true
                docker rm java-app || true
                docker run -d --name java-app -p 8080:8080 java-app:1.0
                '''
            }
        }
    }
}
