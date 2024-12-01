pipeline {
    agent any

    environment {
        NEXUS_URL = 'http://10.0.2.16:8081/repository/go-binaries/'
        NEXUS_USER = 'admin'
        NEXUS_PASSWORD = 'admin123'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/IlyaBridge/8-02-hw.git', credentialsId: 'your-github-credentials-id'
            }
        }

        stage('Build Go Application') {
            steps {
                sh 'go build -o myapp .'
            }
        }

        stage('Upload to Nexus') {
            steps {
                sh """
                curl -u ${NEXUS_USER}:${NEXUS_PASSWORD} -X PUT -T myapp ${NEXUS_URL}myapp
                """
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'myapp', allowEmptyArchive: true
        }
    }
}
