#!/usr/bin/env groovy

pipeline {
    agent any 
    stages {
        stage ('test') {
            steps {
                echo 'Hello World'
            }
        }
         stage ('test1') {
            steps {                
                hipchatSend color: 'GREEN', credentialId: '', message:'"${env.JOB_NAME} ${env.BUILD_NUMBER} status: ${currentBuild.result}"'
            }
        }
    }   
}
