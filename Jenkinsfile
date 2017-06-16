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
                bat '''
                    powershell.exe -command "%WORKSPACE%\\robot_variables.ps1"                  
                   EXIT /b
                   '''   
                load 'RobotVar.txt'                
                hipchatSend message: "<b>Job:</b> ${env.JOB_NAME} , <b>BuildNumber:</b> ${env.BUILD_NUMBER} , <b>status:</b> ${currentBuild.result}, <br /><b>Total:</b> ${ROBOT_TOTAL}, <b>Passed</b>:${ROBOT_PASSED}, <b>Failed:</b>${ROBOT_FAILED}, You can check report here : ${link}"           
            }  
         }      
    }
    
   /* post {        
        always {                
                hipchatSend color: 'YELLOW', credentialId: '', message: '${ROBOT_FAILED} , $ROBOT_TOTAL', room: '', sendAs: '', server: '', v2enabled: true
        }
    }
    */
}
