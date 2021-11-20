pipeline {
    agent any
    
    stage('DeployToProduction') { 
            when { 
                branch 'main' 
            } 
            steps { 
                input 'Deploy to Production?' 
                milestone(1) 
                kubernetesDeploy( 
                    kubeconfigId: 'KUBE_CONFIG0'              
                ) 
            }
                    sh """ 
                    mkdir -p ~/.beki
                    cp ${KUBE_CONFIG_FILE} ~/.beki/config
                    pwd
                    ls -la"""
                    
                    sh """
                   
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
    post {
        success {
            //notifyBuild("SUCCESSFUL")
            sh "echo success"
        }
        failure {
            //notifyBuild("FAILED")
            sh "echo fail"
        }
    }
}
