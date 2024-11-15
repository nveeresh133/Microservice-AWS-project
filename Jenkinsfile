pipeline {
    agent any

    stages {
        stage('Deploy to k8s') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://19EF0D1A9C3D227A50C79429E4909339.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml" 
                sleep 10    
                }
            }
        }
        
        stage('View k8s components') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://19EF0D1A9C3D227A50C79429E4909339.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl get svc -n webapps" 
            }
        }
    }
}
