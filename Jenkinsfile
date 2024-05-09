pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E7586D3AFBE3E67A0070B5EC1EAD1EFC.yl4.ap-south-1.eks.amazonaws.com']]) {
                 sh "kubectl apply -f deployment-service.yml"
                }
                
            }
        }
        
         stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E7586D3AFBE3E67A0070B5EC1EAD1EFC.yl4.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl get svc -n webapps"

               }
            }
        }
    }
}
