pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eksproject', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://12D3D3EAC26378B4C703908B6B409D57.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eksproject', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://12D3D3EAC26378B4C703908B6B409D57.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
