#!/usr/bin/env groovy

pipeline {
    agent any   
    
    stages {
        stage ('test') {
            steps {
                bat '''
                    robot C:\\Install\\RobotDemo-20160129\\RobotDemo\\keyword_driven.robot
                    EXIT /b 0
                    '''                
              
            }  
        }      
    }
    
    post {        
        always {                
                hipchatSend color: 'GREEN', message:" Job : ${env.JOB_NAME} BuildNumber : ${env.BUILD_NUMBER} status: ${currentBuild.ROBOT_TOTAL}, you can check report here : <a href='http://dashboard.cemex.com:81/testing/reports/RobotFrameworkPipeline/${env.BUILD_NUMBER}/Results/report.html'>Open</a> "
        }
    }
}
