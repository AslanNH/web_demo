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
                //sh 'mvn clean package dockerfile:build'
                // 打标签
                //sh 'docker tag web_demo:latest 49.235.114.120:85/tensquare/webdemo:latest'

                //把镜像推送到harbor
                //sh 'docker login -u eric -p Eric123456 49.235.114.120:85'
                //sh 'docker push 49.235.114.120:85/tensquare/webdemo:latest'
                echo '+++++++++++'
            }
        }
    stage('publish') {
                steps {
                   sshPublisher(publishers: [sshPublisherDesc(configName: 'master_server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: "/opt/jenkins_shell/deploy.sh '49.235.114.120:85' 'tensquare/webdemo' 'web_demo' 'latest' '10086'", execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
                }
            }
    }
}
