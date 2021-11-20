pipeline {
    agent any
    
    stages {
        stage('DeployToProduction') { 
            steps{ 
                input 'Deploy to Production?' 
                milestone(1) 
                kubernetesDeploy( 
                    kubeconfigId: 'KUBE_CONFIG1'              
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
               
        
        
    
   
