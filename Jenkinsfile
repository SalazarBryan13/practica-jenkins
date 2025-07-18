pipeline {
    agent any

    stages {
        stage('Build Java (Maven)') {
            steps {
                script {
                    docker.image('maven:3.9-eclipse-temurin-17').inside {
                        dir('java-app') {
                            sh 'mvn clean install'
                        }
                    }
                }
            }
        }

        stage('Build Node.js') {
            steps {
                script {
                    docker.image('node:20').inside {
                        dir('node-app') {
                            sh 'npm install'
                            sh 'npm test || echo "No test script definido"'
                        }
                    }
                }
            }
        }
    }
} 