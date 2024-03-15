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
        bat 'npm install' // Executes a simple batch script to simulate an installation step
      }
    }

    stage('Run React') { // Defines another stage named "Install Dependencies"
      steps {
        bat 'npm run start' // Executes a simple batch script to simulate an installation step
      }
    }
  }
}
