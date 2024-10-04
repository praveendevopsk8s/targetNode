pipeline {
    agent any

    stages {
        stage('Build with Docker') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode = true
                }
            }
            steps {
                sh '''
                cleanWs()
                echo "Building with Docker"
                nod --version 
                npm --version
                npm install
                npm run build
                ls -la				
                '''
            }
        }
        stage('Tests') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode = true
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
