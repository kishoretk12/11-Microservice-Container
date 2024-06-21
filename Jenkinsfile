pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-token', toolName: 'docker') {
                        sh "docker build -t kishoretk12/recommendationservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-token', toolName: 'docker') {
                        sh "docker push kishoretk12/recommendationservice:latest "
                    }
                }
            }
        }
    }
}
