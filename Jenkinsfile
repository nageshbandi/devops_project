pipeline {
    agent any
    stages {
        stage('Cloning Repository') {
            steps {
                git 'https://github.com/nageshbandi/devops_project.git'
            }
        }
        stage('Building Docker Image') {
            steps {
                script {
                    def app = docker.build("devops_project:${env.BUILD_ID}")
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        app.push("${env.BUILD_ID}")
                        app.push("latest")
                    }
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'k8s-deploy-credentials', passwordVariable: 'KUBE_PASSWORD', usernameVariable: 'KUBE_USERNAME')]) {
                    sh 'kubectl config set-credentials $KUBE_USERNAME --username=$KUBE_USERNAME --password=$KUBE_PASSWORD'
                    sh 'kubectl config set-context my-k8s-cluster --cluster=my-k8s-cluster --user=$KUBE_USERNAME'
                    sh 'kubectl config use-context my-k8s-cluster'
                    sh 'kubectl apply -f deployment.yml'
                }
            }
        }
    }
}
