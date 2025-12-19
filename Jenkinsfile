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
               npm ci
               npm run build
               
               ls -ltra
               '''
            }
        }
    }
}
