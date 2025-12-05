pipeline {
    agent any

    tools {
        jdk "Java-17"
        maven "Maven-3.9"
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/YOUR_USERNAME/java-docker-jenkins-maven.git'
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
