pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean'
                sh 'mvn install'
                sh 'mvn package'
                sleep 10
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                sleep 10
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy step'
                sleep 10
            }
        }
        stage('Docker') {
            steps {
                echo 'Image step'
                sleep 10
            }
        }
    }
}