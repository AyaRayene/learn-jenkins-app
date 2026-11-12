pipeline {
    agent any

    stages {
        stage('w/o docker') {
            steps {
                sh 'echo "Without docker"'
                sh 'touch container-no.txt'
            }
        }

        stage('w/ docker') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh 'echo "With docker"'
                sh 'npm --version'
                sh 'touch container-yes.txt'
            }
        }

        stage('check files') {
            steps {
                sh 'ls -la'
            }
        }
    }
}
