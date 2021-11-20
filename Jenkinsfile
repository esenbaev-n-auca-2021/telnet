pipeline {
    agent any
    
    stages {
        stage('DeployToProduction') { 
            steps{
                script{
                    withCredentials([file(credentialsId: 'KUBE_CONFIG', variable: 'KUBE_CONFIG_FILE')]) {  
                    sh """
                    mkdir -p ~/.kube
                    cp ${KUBE_CONFIG_FILE} ~/.kube/config 
                    """
                    }
                }
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
               
        
        
    
   
