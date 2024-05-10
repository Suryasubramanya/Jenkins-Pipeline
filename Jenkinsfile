pipeline {
    agent any

    environment {
        TESTING_ENVIRONMENT = "testing_environment"
        PRODUCTION_ENVIRONMENT = "Subramanya N S"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code with Maven'
            }
             post {
                success {
                    sendEmail('Build Successful')
                }
                failure {
                    sendEmail('Build Failed')
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit'
                echo 'Running integration tests with Selenium'
            }
             post {
                success {
                    sendEmail('Build Successful')
                }
                failure {
                    sendEmail('Build Failed')
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis with Jenkins Plugins'
            }
             post {
                success {
                    sendEmail('Build Successful')
                }
                failure {
                    sendEmail('Build Failed')
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan with SonarQube'
            }
             post {
                success {
                    sendEmail('Build Successful')
                }
                failure {
                    sendEmail('Build Failed')
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server (e.g., AWS EC2 instance)'
            }
             post {
                success {
                    sendEmail('Build Successful')
                }
                failure {
                    sendEmail('Build Failed')
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment'
            }
             post {
                success {
                    sendEmail('Build Successful')
                }
                failure {
                    sendEmail('Build Failed')
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server (e.g., AWS EC2 instance)'
            }
             post {
                success {
                    sendEmail('Build Successful')
                }
                failure {
                    sendEmail('Build Failed')
                }
            }
        }
    }
}

    def sendEmail(String status) {
    mail body: "Pipeline Stage: ${env.STAGE_NAME}\nStatus: ${status}",
             subject: "Pipeline Stage: ${env.STAGE_NAME} - ${status}",
             to: "nssuryasubramanya@gmail.com"
}
