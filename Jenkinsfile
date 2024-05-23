pipeline {
  agent any // This defines the execution environment (any in this case)

environment {
    SONAR_SCANNER_VERSION = '5.0.1.3006'
    SONAR_SCANNER_HOME = "$HOME/.sonar/sonar-scanner-${SONAR_SCANNER_VERSION}-linux"
    PATH = "${SONAR_SCANNER_HOME}/bin:$PATH"
    SONAR_SCANNER_OPTS = "-server"
  }

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

    stage('Setup SonarQube Scanner') {
      steps {
        script {
          sh '''
            curl --create-dirs -sSLo ${env.HOME}/.sonar/sonar-scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-${SONAR_SCANNER_VERSION}-linux.zip
            unzip -o ${env.HOME}/.sonar/sonar-scanner.zip -d ${env.HOME}/.sonar/
            chmod +x ${SONAR_SCANNER_HOME}/bin/sonar-scanner
          '''
        }
      }
    }

    stage('Verify SonarQube Scanner') {
      steps {
        sh 'sonar-scanner --version'
      }
    }

    stage('SonarQube Analysis') {
      steps {
        script {
          sh '''
            sonar-scanner \
              -Dsonar.organization=ggashwin \
              -Dsonar.projectKey=GGAshwin_BloggerLine-Client \
              -Dsonar.sources=. \
              -Dsonar.host.url=https://sonarcloud.io
          '''
        }
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
