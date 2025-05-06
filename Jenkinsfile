pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') { 
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-tokenfinal', namespace: 'webapps', serverUrl: 'https://F0342111EDF14DA39D151299B31F064F.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-tokenfinal', namespace: 'webapps', serverUrl: 'https://F0342111EDF14DA39D151299B31F064F.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
