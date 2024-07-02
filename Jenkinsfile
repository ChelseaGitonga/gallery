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
                sh 'npm instal'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run'
            }
        }

        stage('Test'){
            steps{
                sh 'npm test'
            }
        }
    }
    post {
        failure {
            echo 'Sending an email notification from Jenkins'
            
            step([$class: 'Mailer',
                   notifyEveryUnstableBuild: true,
                   recipients: emailextrecipients([[$class: 'CulpritsRecipientProvider'],
                                                   [$class: 'RequesterRecipientProvider']])])


        }
    }
        
    
} 