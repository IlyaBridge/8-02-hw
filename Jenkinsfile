pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'go test'
                sh 'docker build -t my-image .'
            }
        }
    }
}
