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
        sh 'docker exec -it sonarqube sonar-scanner -Dsonar.projectKey=bloggerline-client -Dsonar.sources=. -Dsonar.host.url=http://54.145.74.209:9000 -Dsonar.token=sqp_e1a1e0dd13d919fb938c78133689c22dbceda858'
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
