pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                script {
                    // The below will clone your repo and will be checked out to master branch by default.
                    git credentialsId: 'jenkins-user-github', url: 'https://github.com/nageshbandi/devops_project.git'
                    // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
                    sh "ls -lart ./*" 
                    // List all branches in your repo. 
                    sh "git branch -a"
                    // Checkout to a specific branch in your repo.
                    sh "git checkout main"
                    }
                }
        }
        // ...
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
