pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(
                    caCertificate: '',
                    clusterName: 'EKS1',
                    contextName: '',
                    credentialsId: 'k8-token',
                    namespace: 'webapps',
                    restrictKubeConfigAccess: false,
                    serverUrl: 'https://142875DE0DDF13169AE6E8BAE856BEE6.gr7.ap-south-1.eks.amazonaws.com'
                ) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeConfig(
                    caCertificate: '',
                    clusterName: 'EKS1',
                    contextName: '',
                    credentialsId: 'k8-token',
                    namespace: 'webapps',
                    restrictKubeConfigAccess: false,
                    serverUrl: 'https://142875DE0DDF13169AE6E8BAE856BEE6.gr7.ap-south-1.eks.amazonaws.com'
                ) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
