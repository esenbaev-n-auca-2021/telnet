pipeline {
    agent any
    
    stages {
        stage('DeployToProduction') { 
            steps{
               kubernetesDeploy(
                   kubeconfig: 'kubeconfig1'
                   )
               
                    }
                }
            
        
        stage(app) {
            steps{
                script{   
                    sh """
                    mkdir -p ~/.kube
                    cp ${KUBE_CONFIG_FILE} ~/.kube/config                
                    kubectl exec nginx -- /bin/bash
                    sudo yum update -y
                    sudo yum install telnet -y
                    sleep 5
                    telnet version                    
                    """
                }   
                }
        }
    }
}
               
        
        
    
   
