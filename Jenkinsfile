pipeline {
    agent any
    stages {
            stage('Clone repository') {
            steps {
                    git branch: 'main', url: 'https://github.com/nageshbandi/devops_project.git'
                    }
                sshagent(['mac-book']) {
                                sh "scp -o stricthostkeychecking=no hello.py bandinageswarrao@bandis-MacBook-Air.local:/Users/bandinageswarrao/linux_learn"
                                sh "ls -ltr"
                                sh "./hello.py"
                                }
                }
            stage("Execute"){
                    sh "chmod +x hello.py"
                    sh "./hello.py"
                    } 
        }
}
