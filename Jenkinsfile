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
                sh 'mvn clean package'
            }
        }
        stage('move') {
            steps {
               sh 'mv /var/lib/jenkins/workspace/web_dmeo_pipeline/target/web_demo-0.0.1-SNAPSHOT.jar /data/web_demo-0.0.1-SNAPSHOT.jar '
               sleep 1
            }
        }
         stage('publish') {
            steps {
                dir('/data') {
                    sh 'kill -9 `ps -ef | grep java |grep web_demo | awk '{print$2}'`'
                    sh 'JENKINS_NODE_COOKIE=dontKillMe nohup java -jar web_demo-0.0.1-SNAPSHOT.jar >web_demo.log 2>&1 &'
                }
            }
        }
    }
}
