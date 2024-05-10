pipeline {
  agent any

  environment {
    TESTING_ENVIRONMENT = "testing_environment"
    PRODUCTION_ENVIRONMENT = "Subramanya N S"
  }

  stages {
    stage('Build') {
      steps {
        script {
          echo 'Building code using Maven'
          sendEmail('Build Successful')
        }
      }
      post {
        failure {
          sendEmail('Build Fail')
        }
      }
    }

    stage('Unit, and Integration Tests') {
      steps {
        script {
          echo 'Using JUnit to execute unit tests'
          echo 'Using Selenium to conduct integration testing'
          sendEmail('Build Successful')
        }
      }
      post {
        failure {
          sendEmail('Build Fail')
        }
      }
    }

    stage('Code Interpretation') {
      steps {
        script {
          echo 'Code analysis using the Jenkins Plugins'
          sendEmail('Build Successful')
        }
      }
      post {
        failure {
          sendEmail('Build Fail')
        }
      }
    }

    stage('Security Scan') {
      steps {
        script {
          echo 'Conducting a security audit with SonarQube'
          sendEmail('Build Successful')
        }
      }
      post {
        failure {
          sendEmail('Build Failed')
        }
      }
    }

    stage('Implement to Staging') {
      steps {
        script {
          echo 'Deploy to staging server'
          sendEmail('Build Successful')
        }
      }
      post {
        failure {
          sendEmail('Build Failed')
        }
      }
    }

    stage('Testing Integration for Staging') {
      steps {
        script {
          echo 'executing integration tests in a staging setting'
          sendEmail('Build Successful')
        }
      }
      post {
        failure {
          sendEmail('Build Fail')
        }
      }
    }

    stage('Deploy to Production') {
      steps {
        script {
          echo 'Deploy to production server'
          sendEmail('Build Successful')
        }
      }
      post {
        failure {
          sendEmail('Build Fail')
        }
      }
    }
  }
}

def sendEmail(String status) {
  mail body: "Pipeline Stage: ${env.STAGE_NAME}\\nStatus: ${status}",
       subject: "Pipeline Stage: ${env.STAGE_NAME} - ${status}",
       to: "nssuryasubramanya@gmail.com"
}
