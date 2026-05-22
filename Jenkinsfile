pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            reuseNode true
        }
    }
    
    environment {
        BUILD_FILE_NAME = "laptop.txt"
    }

    stages {
        stage('Build') {

            steps {
                echo 'Building the app ...'
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing the app ...'
                sh '''
                    npm test
                '''
            }
        }
    }
    post{
        success{
            archiveArtifacts artifacts: 'build/**'
        }
        cleanup {
            cleanWs()
        }
    }
}
