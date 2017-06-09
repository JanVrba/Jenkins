#!/usr/bin/env groovy

pipeline {
    agent any 
    stages {
        stage ('test') {
            steps {
                echo 'Hello World'
                hipchatSend color: 'GREEN', credentialId: '', message: hipchatSend '"${env.JOB_NAME} ${env.BUILD_NUMBER} status: ${currentBuild.result}"'

            }
        }
    }   
}
