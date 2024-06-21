pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-Cluster', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://6637E6BDA687DDBFB302510804DAECFC.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-Cluster', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://6637E6BDA687DDBFB302510804DAECFC.gr7.us-east-1.eks.amazonaws.com']]) {

                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
