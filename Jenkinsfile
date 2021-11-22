pipeline {
    agent any
    
    stages {
        stage('DeployToProduction') { 
            steps{
               withCredentials([usernamePassword(credentialsId: 'webserver_login', usernameVariable: 'USERNAME', passwordVariable: 'USERPASS')]) {
                            script {
                                sh "sshpass -p '$USERPASS' -v ssh -o StrictHostKeyChecking=no $USERNAME@$dev_ip \"kubectl get nodes\"" 
                                sh "sshpass -p '$USERPASS' -v ssh -o StrictHostKeyChecking=no $USERNAME@$dev_ip \"kubectl exec --stdin --tty nginx -- /bin/bash\""
                                sh "sshpass -p '$USERPASS' -v ssh -o StrictHostKeyChecking=no $USERNAME@$dev_ip \"sudo apt install telnet -y\""
                                
                    } 
                }
            }
        }
            
        
//         stage(app) {
//             steps{
//                 script{   
//                     sh """
//                     mkdir -p ~/.kube
//                     cp ${KUBE_CONFIG_FILE} ~/.kube/config                
//                     kubectl exec nginx -- /bin/bash
//                     sudo yum update -y
//                     sudo yum install telnet -y
//                     sleep 5
//                     telnet version                    
//                     """
//                 }   
//                 }
//         }
    }
}
               
        
        
    
   
