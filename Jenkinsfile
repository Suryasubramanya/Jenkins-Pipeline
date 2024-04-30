pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                //Maven to build the code
                sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests using JUnit
                sh 'mvn test'

                // Run integration tests using Selenium
                sh 'mvn verify'
            }
        }

        stage('Code Analysis') {
            steps {
                // Analyze the code using SonarQube
                sh 'mvn sonar:sonar'
            }
        }

        stage('Security Scan') {
            steps {
                // Perform a security scan using OWASP ZAP
                sh 'zap-cli quick-scan --url http://124.148.225.143/github-webhook/'
            }
        }

        stage('Deploy to Staging') {
            steps {
                // Deploy the application to a staging server using Docker
                sh 'docker build -t your-app:staging .'
                sh 'docker run -d -p 8080:8080 my-app:staging'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment using Selenium
                sh 'mvn verify -Denvironment=staging'
            }
        }

        stage('Deploy to Production') {
            steps {
                // Deploy the application to a production server using Docker
                sh 'docker build -t your-app:latest .'
                sh 'docker run -d -p 80:8080 your-app:latest'
            }
        }
    }

    post {
        always {
            // Send notification emails
            emailext subject: 'Jenkins Pipeline Report',
                      body: 'See the attached build log for details.',
                      attachLog: true,
                      to: 's223113345@deakin.edu.au'
        }
    }
}
