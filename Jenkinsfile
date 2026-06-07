pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://3734C86559E701B49ACEDDE9FDFE1E4F.gr7.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://3734C86559E701B49ACEDDE9FDFE1E4F.gr7.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
