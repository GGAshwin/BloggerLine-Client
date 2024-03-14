pipeline {
    agent any

    stages {
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
