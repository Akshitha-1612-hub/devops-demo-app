pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t kesariakshitha/devops-demo-app .'
            }
        }

        stage('Push Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-pass', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh '''
                    echo $PASS | docker login -u $USER --password-stdin
                    docker push kesariakshitha/devops-demo-app
                    '''
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}
    

stage('Deploy to Kubernetes') {
    steps {
        // Use kubeconfig credential
        withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECONFIG')]) {
            sh 'kubectl apply -f deployment.yaml'
        }
    }
}        
            
                
            
        

 
            
                
           
       

        
           
            
                    
                    
                    
                    
                
            
        

        
            
                
             
            
    
