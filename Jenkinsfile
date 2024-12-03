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
                sh "docker build -t mavenwebapp"
            }
        }
            
    }
}
