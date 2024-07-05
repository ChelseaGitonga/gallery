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
            echo 'Pipeline run successfully'
             step(
                slackSend color: 'good', message: 'Deployment successful. Build ID: dccfc49, Link to Render - https://gallery-s0sr.onrender.com'
             )      
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