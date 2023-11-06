pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    environment {
        registry = '939083599624.dkr.ecr.us-east-1.amazonaws.com/pipeline'
        registryCredential = jenkins
        dockerImage = ''
    }
    stages {
        stage('checkout'){
            steps {
                git branch: 'main', url: 'https://github.com/Freensh/helloworld_pipeline.git'
            }
        }
        stage('Code Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                sleep 10
            }
        }
        stage('Build Image') {
            steps {
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
        stage('Store Docker Image') {
            steps {
                script{
                    docker.withRegistry("https://"+registry,"ecr:us-east-1:"+registryCredential) {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}