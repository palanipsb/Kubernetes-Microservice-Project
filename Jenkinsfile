pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'aks-microservice-proj', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'aks-microservice-proj-dns-ijvv65pm.hcp.southindia.azmk8s.io']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'aks-microservice-proj', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'aks-microservice-proj-dns-ijvv65pm.hcp.southindia.azmk8s.io']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
    
    
}
