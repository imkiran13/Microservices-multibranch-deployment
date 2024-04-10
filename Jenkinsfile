pipeline {
    agent any

    stages {
        stage('deploy to k8') {
            steps {
             withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9D0270BF3CF11BCBA40CD6F1FEA1FA29.gr7.ap-south-1.eks.amazonaws.com']]) {
              sh "kubectl apply -f deployment-service.yml"
            }  
            }
        }
        stage('verify deployment') {
            steps {
             withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9D0270BF3CF11BCBA40CD6F1FEA1FA29.gr7.ap-south-1.eks.amazonaws.com']]) {
               sh "kubectl get svc -n webapps"
            }  
            }
        }
    }
}
