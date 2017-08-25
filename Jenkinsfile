#!/usr/bin/env groovy

import org.json.JSONObject
import groovy.xml.MarkupBuilder 
import groovy.util.XmlParser

pipeline {
    environment {

        // bitbucket settings  
        def branchName = "master"
        def repoName = "dcmqa_ta"
        // def wrkspc = "${env.WORKSPACE}"

    }

    agent any     

    stages {
        /*
        stage('PullScript') {
            steps {             
                checkout poll: false, 
                scm: [$class: 'GitSCM', 
                    branches: [[name: "*" + branchName]], 
                    doGenerateSubmoduleConfigurations: false, 
                    extensions: [[$class: 'CloneOption', 
                                                depth: 0, 
                                                noTags: false, 
                                                reference: '', 
                                                shallow: false, 
                                                timeout: 60]], 
                    submoduleCfg: [], 
                    userRemoteConfigs: [[credentialsId: '2ac4ae14-9741-469b-892e-0ab81123ce6c', url: 'https://bitbucket.org/cemex/' + repoName  + '.git']]]
            }
        }

'        stage('Execute Scripts') {'
            steps {  
                echo "Start Automated Testing"
                withCredentials([usernamePassword(credentialsId: '92fba331-6458-46b6-bf34-c9ed89d358b2', passwordVariable: 'DB_PASSWORD', usernameVariable: 'DB_USER')]) {
                    bat '''
                        call robot --removeKeywords name:DatabaseLibrary.connect* -i Regression -e Perfecto -e iOS -e Android -d Results ./
                        EXIT /B 0
                    '''
                }
            }

        }

        stage('Publish RobotFW results') {
            steps {
                echo "Start publishing RobotFW results"
//                 step([$class : 'RobotPublisher',
                        outputPath : "${WORKSPACE}/Results",
                        outputFileName : "*.xml",
                        disableArchiveOutput : false,
                        passThreshold : 50,
                        unstableThreshold: 50,
                        otherFiles : "*.png",
                        otherFiles : "*.html",])
            }
        }

        stage('Copy RobotFW results to Dashboard') {
            steps {
                echo "Starting of copy results..."
                bat '''
                    
                    SET source=/D/Jenkins/Slaves/Poc/workspace/QAAutomation/RobotFrameworkPipeline/Results/*
                    SET destination=/srv/www/htdocs/testing/reports/RobotFrameworkPipeline
                    SET privatekey=C:\\Users\\Public\\.ssh\\dashboard.ppk
                    
                    ssh -v -o StrictHostKeyChecking=no -i %privatekey% jenkins@10.26.103.44 mkdir %destination%/%BUILD_NUMBER%
                    ssh -v -o StrictHostKeyChecking=no -i %privatekey% jenkins@10.26.103.44 mkdir %destination%/%BUILD_NUMBER%/Results

                    scp -v -i %privatekey% %source% jenkins@10.26.103.44:%destination%/%BUILD_NUMBER%/Results                    
                   
                '''
            }
        }

        */

        stage('Send Hipchat message') {
            steps   {
                echo "Getting ROBOTFW variables from output file..."
                bat '''
                        powershell.exe -NonInteractive -ExecutionPolicy Bypass -Command '%WORKSPACE%\\robot_variables.ps1'
                        EXIT /b
                    '''                                
            }      
        }               
                        
    }                
               
} 
