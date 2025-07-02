pipeline {
    agent {
            label 'agent-1'
        }

    tools {
        maven 'maven3.9'
        jdk 'jdk17'
    }

    stages {
        stage('Compilee') {
            steps {
                sh 'mvn compile'
            }
        }        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }
}

