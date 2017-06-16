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
                    powershell.exe -command "C:\\Program Files (x86)\\Jenkins\\workspace\\TestPipeline\\robot_variables.ps1"                  
                   EXIT /b
                   '''   
                load 'RobotVar.txt'
                hipchatSend message:"Total: ${ROBOT_TOTAL}, Passed: ${ROBOT_PASSED}, Failed: ${ROBOT_FAILED}"            
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
