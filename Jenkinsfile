pipeline {
    agent any

    environment {
        DOCKER_HUB_USER = 'kesariakshitha'
        DOCKER_IMAGE = 'kesariakshitha/devops-demo-app'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Akshitha-1612-hub/devops-demo-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DOCKER_HUB', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }

        stage('Setup Kubeconfig') {
            steps {
                withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECONFIG')]) {
                    sh '''
                        echo "Using kubeconfig from Jenkins credentials"
                        kubectl config view
                    '''
                }
            }
        }

        stage('Check Kubernetes Cluster') {
            steps {
                sh '''
                    echo "Current context:"
                    kubectl config current-context
                    echo "Nodes in the cluster:"
                    kubectl get nodes
                '''
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }

    }

    post {
        always {
            echo 'Pipeline finished'
        }
    }
}        
    

   
                
        
    
             
                
            
        

 
            
                
           
       

        
           
            
                    
                    
                    
                    
                
            
        

        
            
                
             
            
    
