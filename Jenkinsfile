pipeline {
    agent {
        label 'ec2'
    }

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                   withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKs-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://715CE412D4834D64443BEB6BBB7C732E.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    }
            }
        }
        
        stage('verify Deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKs-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://715CE412D4834D64443BEB6BBB7C732E.gr7.us-east-1.eks.amazonaws.com']]) {
                         sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
