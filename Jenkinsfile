pipeline {
    agent any

    tools {
        golang 'go'  // Убедитесь, что Go установлен и настроен в Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/IlyaBridge/8-02-hw.git'
            }
        }
        stage('Build') {
            steps {
                sh 'go build -o myapp'
            }
        }
        stage('Upload to Nexus') {
            steps {
                script {
                    def server = Artifactory.server 'nexus'
                    def uploadSpec = """{
                        "files": [
                            {
                                "pattern": "myapp",
                                "target": "go-binaries/"
                            }
                        ]
                    }"""
                    server.upload(uploadSpec)
                }
            }
        }
    }
}
