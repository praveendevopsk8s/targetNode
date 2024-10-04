pipeline {
    agent any

    stages {
        stage('Build with Docker') {
            agent {
                Docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh '''
                cleanWs()
                echo "Building with Docker"
                noe --version 
                npm --version
                npm install
                '''
            }
        }
        stage('Tests') {
            agent {
                Docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh '''
                test -f build/index.html
                npm test
                '''
            }
        }        
    }
}
