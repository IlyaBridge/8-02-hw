pipeline {
    agent any
 
    environment {
        NEXUS_URL = 'http://10.0.2.16:8081/repository/go-binaries'
        NEXUS_USER = 'admin'
        NEXUS_PASSWORD = '88520'
    }
 
    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/IlyaBridge/8-02-hw.git', branch: 'main'
            }
        }
        stage('Build Binary') {
            steps {
                sh 'go build -o go-app .'
            }
        }
        stage('Upload to Nexus') {
            steps {
                script {
                    def fileName = "go-app"
                    sh """
                       curl -v -u ${NEXUS_USER}:${NEXUS_PASSWORD} --upload-file ${fileName} ${NEXUS_URL}/${fileName}
                    """
                }
            }
        }
    }
}
