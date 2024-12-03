pipeline {  
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url:  'https://github.com/Ashaikh609/maven-web-app.git'
            }
        }

    stage('Build Application') {
            steps {
                sh "mvn clean package"
            }
        }
    
    stage('Docker image Build') {
            steps {
                withCredentials([usernameColonPassword(credentialsId: 'Docker_credentials', variable: '')])
                sh "docker build -t mavenwebapp ."
                sh "docker tag mavenwebapp altamash212/mavenwebapp"
                sh "docker push mavenwebapp"
            
            }
        }
            
    }
}
