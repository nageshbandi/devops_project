pipeline {
    agent any
    stages {
            stage('Clone repository') {
            steps {
                git branch: 'master',
                credentialsId: 'my-credentials',
                url: 'https://github.com/myuser/myrepo.git'
            }
           }
        }
}
