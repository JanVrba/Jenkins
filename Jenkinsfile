#!/usr/bin/env groovy

pipeline {
    agent any
    def Number = '90'
    stages {
        stage ('test') {
            steps {
                echo 'Hello World'
            }
        }
    }
    post {        
        always {                
                hipchatSend color: 'GREEN', message:" Job : ${env.JOB_NAME} BuildNumber : ${env.BUILD_NUMBER} status: ${currentBuild.result}, you can check report here : <a href='http://dashboard.cemex.com:81/testing/reports/RobotFrameworkPipeline/${Number}/Results/report.html'>Open</a> "
            }
    }
}
