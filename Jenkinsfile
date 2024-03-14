pipeline {
    agent any
        stage('Checkout Code') {
            steps {
                git branch: 'master', // Replace with your branch name (if not main)
                    url: 'https://github.com/GGAshwin/BloggerLine-Client.git'
            }
        }
    stages {
        stage('Install Dependencies') {
            steps {
               sh 'echo done'
            }
        }
    }
}
