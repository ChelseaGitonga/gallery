pipeline {
    agent any
    
    tools{
        nodejs 'NodeJS'
    }
    
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/ChelseaGitonga/gallery'
            }
            
        }
        stage('Build') {
            steps {
                
                sh 'npm install'
                sh 'npm run'
            }
        }
    }
}