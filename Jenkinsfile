pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master', // Replace with your branch name (if not main)
                    url: 'https://github.com/GGAshwin/BloggerLine.git'
            }
        }
        stage('Install Dependencies') {
            steps {
               sh 'cd ./client && npm install'
            }
        }
        stage('Deploy'){
            steps{
                sh 'pm2 start " cd ./client && npm start"'
                sh 'pm2 save'
            }
        }
    }
}
