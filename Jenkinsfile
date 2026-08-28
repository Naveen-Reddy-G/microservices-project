pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eksproject', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://21CF167C1EAE6C6CB48C66C78E7B11A0.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eksproject', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://21CF167C1EAE6C6CB48C66C78E7B11A0.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
