pipeline {
    agent any

    stages {
        stage('Build') {
            echo "build stage"
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('Test') {
            echo "test stage"
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                sh '''

                    ls -la
                    test -f build/index.html
                    npm test
                '''
            }
        }
    }
}