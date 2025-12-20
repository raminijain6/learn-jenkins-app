pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:20-alpine'
                    reuseNode true
                }
            }
            steps {
               sh'''
               ls -ltra
               npm --version
               node --version
               npm cache clean --force
               npm ci
               npm run build
               
               ls -ltra
               npm test
               '''
            }
        }
        stage("Test"){
            steps{
                sh '''
                echo 'Test Stage'
                ls -ltra ./build index.html
                npm test
                '''

            }
        }
    }
}
