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
            curl --create-dirs -sSLo $HOME/.sonar/sonar-scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-${SONAR_SCANNER_VERSION}-linux.zip
            unzip -o $HOME/.sonar/sonar-scanner.zip -d $HOME/.sonar/
            chmod +x $SONAR_SCANNER_HOME/bin/sonar-scanner
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
  -Dsonar.projectKey=bloggerline-client \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://54.145.74.209:9000 \
  -Dsonar.token=sqb_eb6d158a46f7810416e779bccfefb5ce111bd349
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
