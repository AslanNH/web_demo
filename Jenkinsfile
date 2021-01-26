pipeline {
    agent any

    stages {
        stage('pull code') {
            steps {
                 git credentialsId: '139b798b-5333-4bee-be98-212a2ccaf41e', url: 'https://github.com/AslanNH/web_demo.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package dockerfile:build'
            }
        }

    }
}
