pipeline {
    agent any
    
    environment {
        BUILD_FILE_NAME = "laptop.txt"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the app ...'
                sh '''
                    npm install
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
