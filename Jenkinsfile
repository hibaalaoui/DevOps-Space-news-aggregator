pipeline {
    agent any
    tools {
        maven 'maven'
    }
    environment {
        IMAGE_NAME = 'hibaalaouii/devops-integration'
    }
    stages {
        stage('Build Maven') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/hibaalaoui/DevOps-Space-news-aggregator']])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image') {
            steps {
                script {
                    sh "docker build --no-cache -t ${env.IMAGE_NAME} ."
                }
            }
        }
        stage('Push image to hub') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                        sh "echo ${dockerhubpwd} | docker login -u hibaalaouii --password-stdin"
                    }
                    sh "docker push ${env.IMAGE_NAME}"
                }
            }
        }
        stage('Deploy with Docker Compose') {
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/hibaalaoui/DevOps-Space-news-aggregator']])
                    sh 'docker compose down'
                    sh 'docker compose up -d'
                }
            }
        }
    }
}
