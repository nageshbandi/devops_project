pipeline {
    agent any
    stages {
            stage('Clone repository for dev') {
            steps {
                    git branch: 'main', url: 'https://github.com/nageshbandi/devops_project.git'
                    sshagent(['mac-book']) {
                                sh "scp -o stricthostkeychecking=no hello.py bandinageswarrao@bandis-MacBook-Air.local:/Users/bandinageswarrao/linux_learn"
                                sh "ls -ltr"
                                sh "chmod +x hello.py"
                                sh "python3 hello.py"
                                }
                    }
                }
            stage('test stage') {
            steps {
                   sh "echo 'this is test stage '"
                    }
                }
        }
}
