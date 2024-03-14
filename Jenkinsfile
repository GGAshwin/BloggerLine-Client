pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master', // Replace with your branch name (if not main)
                    url: 'https://github.com/GGAshwin/BloggerLine-Client.git'
            }
        }
        stage('Install Dependencies') {
            steps {
               sh 'npm install'
            }
        }
        stage('Deploy'){
            steps{
                sh 'pm2 start "npm run start"'
                sh 'pm2 save'
            }
        }
    }
}
