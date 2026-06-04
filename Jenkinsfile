pipeline {
    agent any

    stages {
        stage('Build') {

            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                echo "build stage"
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

            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                echo "test stage"
                sh '''

                    ls -la
                    test -f build/index.html
                    npm test
                '''
            }
        }
    }
}