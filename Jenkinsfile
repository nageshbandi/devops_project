pipeline {
    agent any
    stages {
            stage('Clone repository') {
            steps {
                    git branch: 'main', url: 'https://github.com/nageshbandi/devops_project.git'
                    }
                }
            stage("Execute"){
                    sh "chmod +x hello.py"
                    sh "./hello.py"
                    } 
        }
}
