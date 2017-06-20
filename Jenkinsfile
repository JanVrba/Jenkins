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
                    powershell.exe -command '%WORKSPACE%\\robot_variables.ps1'                  
                   EXIT /b
                   '''   
                load 'RobotVar.txt' 
                ROBOT_TESTS = """
                1 Customer Information : Add new jobsite request : FAIL,
 1 Customer Information : Verify new jobsite request was created : FAIL,
 3 Orders Product Catalog : ORDER REQUEST - HappyPATH : FAIL,
 3 Orders Product Catalog : ORDER REQUEST - Repeat : FAIL,
 3 Orders Product Catalog : ORDER REQUEST - Draft Delete : FAIL,
 3 Orders Product Catalog : PP HappyPath : FAIL,
 3 Orders Product Catalog : Delete Project Profile : FAIL,
 4 Delivery Schedule : Basic Display : PASS,
 4 Delivery Schedule : Import valid excel file : PASS,
 4 Delivery Schedule : Import excel file with invalid Material type : FAIL,
 """


                hipchatSend message: """
                <b>Job:</b> ${env.JOB_NAME} , 
                <b>BuildNumber:</b> ${env.BUILD_NUMBER} , 
                <b>status:</b> ${currentBuild.result},<br /> 
                <b>Total:</b> ${ROBOT_TOTAL}, 
                <b>Passed</b>:${ROBOT_PASSED}, 
                <b>Failed:</b>${ROBOT_FAILED}, 
                You can check report here : link,<br />
                ${ROBOT_TESTS}
                """           
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
