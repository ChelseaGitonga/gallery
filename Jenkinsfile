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

        stage('Deploy') {
            steps {
                script {
                    def url = 'https://gallery-s0sr.onrender.com/'
                    openLink(url)
                }
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