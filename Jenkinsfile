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
                 bat '''
                    scp C:\\Users\\jvrba\\service.txt jvrba@104.47.153.223:~\\sevice2.txt
             }
       }      
    }
    
    post {        
        always {                
                hipchatSend color: 'GREEN', message:" Job : ${env.JOB_NAME} BuildNumber : ${env.BUILD_NUMBER} status: ${currentBuild.result}, you can check report here : <a href='http://dashboard.cemex.com:81/testing/reports/RobotFrameworkPipeline/${env.BUILD_NUMBER}/Results/report.html'>Open</a> "
        }
    }
}
