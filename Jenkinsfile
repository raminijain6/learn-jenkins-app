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
            agent{
                docker{
                    image 'node:20-alpine'
                     reuseNode true
                }
            }

            steps{
                echo "Test Stage"
                sh '''
                
               
                test -f build/index.html
                npm test
                '''

            }
        }
    }
}
