pipeline {
    agent any
    tools {
        nodejs "Node.js"
    }
    environment {
        recipientEmails = "kephaokari@gmail.com, rkapps47@gmail.com"
    }
    stages {
        
        stage('clone repository') {
            steps { 
                git 'https://github.com/kepha-okari/gallery.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
            
            post{
                always{
                    slackSend( channel: "#jenkins-notifications", token: "slack_webhook token", color: "good", message: "Gallery dependencies installed")
                }    
            }
            
        }
        
        stage ('Build'){
            steps {
                echo 'run server here'
                // sh 'node server'     
            }
        }
    
    }
    
    post{
        always{
            mail to: "${recipientEmails}",
            subject: "Jenkins Gallery App",
            body: "pipeline finishccced running"
        }
    }
    

  
}