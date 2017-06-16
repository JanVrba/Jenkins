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
                hipchatSend color: 'YELLOW', message: '${ROBOT_TOTAL} , $ROBOT_TOTAL', '${CHANGES_OR_CAUSE}'              
            }  
        }      
    }
    
    post {        
        always {                
                hipchatSend color: 'YELLOW', credentialId: '', message: '${ROBOT_TOTAL} , $ROBOT_TOTAL', room: '', sendAs: '', server: '', v2enabled: true
        }
    }
}
