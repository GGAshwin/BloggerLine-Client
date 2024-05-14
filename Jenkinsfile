pipeline {
  agent any // This defines the execution environment (any in this case)

  stages {
    stage('Checkout Code') { // Defines a stage named "Checkout Code"
      steps {
        git branch: 'main', // Fetches code from the specified branch
          url: 'https://github.com/GGAshwin/BloggerLine-Client.git' // URL of the Git repository
      }
    }

    stage('Install Dependencies') { // Defines another stage named "Install Dependencies"
      steps {
        sh 'npm install' // Executes a simple batch script to simulate an installation step
      }
    }

    stage('Build React') { // Defines another stage named "Install Dependencies"
      steps {
        sh 'npm run build' // Executes a simple batch script to simulate an installation step
      }
    }

    stage('Sonar Scan'){
      steps{
        // sh 'export PATH=$PATH:/home/sonarqube/"sonar-scanner-5.0.1.3006-linux"/bin'
                    // sh 'sudo chmod +x ${SONAR_SCANNER_PATH}'
        sh 'sudo chmod 777 ${SONAR_SCANNER_PATH}/sonar-scanner && export PATH=$PATH:${SONAR_SCANNER_PATH} && sonar-scanner \
  -Dsonar.projectKey=bloggerline-client \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://54.145.74.209:9000 \
  -Dsonar.token=sqp_00355fb3902c3c14b22f3b650186b83553f5eb36'
        }
    }

    stage('Deploy') { // Defines another stage named "Install Dependencies"
      steps {
        sh "sudo rm -rf /var/www/bloggerline/*"
        sh 'sudo cp -r "${WORKSPACE}/build/" /var/www/bloggerline/'
      }
    }
  }
}
