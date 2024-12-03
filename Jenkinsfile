pipeline {  
    agent {
        label 'Ansible-Node'
    }    
    tools{
        maven "Maven-3.9.6"
    }
    stages {
        stage('Clone') {
            steps {
               git 'https://github.com/Ashaikh609/maven-web-app.git'
            }
        }
        stage('Build') {
            steps {
               sh 'mvn clean package'
            }
        }        
        stage('Create Image'){
            steps{
               steps {
                	script {
                		sh 'ansible-playbook task.yml'
                	}
                }
            }
        }
    }
}
