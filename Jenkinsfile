pipeline {
    agent any
    
    tools {
        nodejs 'NodeJS'
    }
    
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/ChelseaGitonga/gallery'
            }
            
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run'
            }
        }

        stage('Test') {
            steps{
                sh 'npm test'
            }
        }

        stage('Deploy to render') {
            steps{
                sh 'curl -X POST -d "" https://api.render.com/deploy/srv-cq1964qju9rs73bi5ir0?key=EN0AK56jcC0'
            }
        }


    }
    post {
        success {
            echo 'Slack Notification'

            slackSend channel: 'chelsea_ip1', 
                      color: 'good', 
                      message: "Job: ${env.JOB_NAME} Build: ${env.BUILD_NUMBER} Link to render - https://gallery-s0sr.onrender.com" 
  
        }

        failure {
            echo 'Sending an email notification from Jenkins'
            
            step([$class: 'Mailer',
                   notifyEveryUnstableBuild: true,
                   recipients: emailextrecipients([[$class: 'CulpritsRecipientProvider'],
                                                   [$class: 'RequesterRecipientProvider']])])


        }
    }
          
} 