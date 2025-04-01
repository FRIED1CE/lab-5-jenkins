pipeline{
    agent any
        stages{
            stage("k8s"){
                steps{
                    withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'cluster', contextName: '', credentialsId: 'be82a716-dd4d-4e1f-a98b-ebe5c6a29370', namespace: 'default', serverUrl: 'https://52D2317494A52E07FBFBE0F76ABB170F.gr7.eu-west-1.eks.amazonaws.com']]) 
                    {
                    sh 'curl -LO "https://storage.googleapis.com/kubernetes-release/release/v1.20.5/bin/linux/amd64/kubectl"'
                    sh 'chmod u+x ./kubectl'
                    sh './kubectl get nodes'
                    sh './kubectl create -f pod_run'
                    sh './kubectl get pods'
                    }
                }    
        }
    }
}
