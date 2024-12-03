pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Ashaikh609/maven-web-app.git'
            }
        }

        stage('Build Application') {
            steps {
                sh "mvn clean package"
            }
        }

        stage('Docker Image Build and Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'Docker_credentials', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    // Docker login
                    sh "echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin"
                    // Build Docker image
                    sh "docker build -t altamash212/mavenwebapp ."
                    // Push Docker image
                    sh "docker push altamash212/mavenwebapp"
                }
            }
        }
    }
}
