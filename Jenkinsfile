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
    }
}