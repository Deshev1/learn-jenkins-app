pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            reuseNode true
        }
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
                    test -f build/index.html
                    npm test
                '''
            }
        }
    }
    post{
        cleanup {
            cleanWs()
        }
    }
}
