pipeline {
    agent any
    
    environment {
        BUILD_FILE_NAME = "laptop.txt"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building a new laptop...'
                sh '''
                    mkdir -p build
                    echo "mainboard" >> build/$BUILD_FILE_NAME
                    cat build/$BUILD_FILE_NAME
                    echo "display" >> build/$BUILD_FILE_NAME
                    cat build/$BUILD_FILE_NAME
                    echo "keyboard" >> build/$BUILD_FILE_NAME
                    cat build/$BUILD_FILE_NAME
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing laptop...'
                sh '''
                    test -f build/$BUILD_FILE_NAME
                    grep -i "mainboard" build/$BUILD_FILE_NAME
                    grep -i "display" build/$BUILD_FILE_NAME
                    grep -i "keyboard" build/$BUILD_FILE_NAME
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
