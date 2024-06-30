pipeline {
    agent any
    
    tools {
        nodejs 'NodeJS'
    }
    
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/ChelseaGitonga/gallery'
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
    }
}