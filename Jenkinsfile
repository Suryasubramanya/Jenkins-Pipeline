pipeline {
    agent any

    environment {
        // Define environment variables
        STAGING_SERVER = 'staging.example.com'
        PRODUCTION_SERVER = 'production.example.com'
        SONAR_HOST_URL = 'http://sonar.example.com'
        SONAR_LOGIN = 'your_sonar_login_token'
    }

    tools {
        // Make sure Maven and JDK are installed and configured in Jenkins Global Tool Configuration
        maven 'Maven3'
        jdk 'JDK8'
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Checks out the source code from the repository
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube...'
                sh "mvn sonar:sonar -Dsonar.projectKey=YourProjectKey -Dsonar.host.url=${SONAR_HOST_URL} -Dsonar.login=${SONAR_LOGIN}"
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP ZAP...'
                sh 'zap-baseline.py -t http://your-staging-url'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server...'
                sh 'scp target/myapp.war ${STAGING_SERVER}:/var/www/html/'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                sh 'ssh ${STAGING_SERVER} "cd /var/www/html/ && java -jar myapp.war"'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server...'
                sh 'scp target/myapp.war ${PRODUCTION_SERVER}:/var/www/html/'
            }
        }
    }

    post {
        always {
            echo 'Sending email notifications...'
            mail to: 's223113345@deakin.edu.au',
                 subject: "Build ${currentBuild.fullDisplayName} finished",
                 body: "Build status: ${currentBuild.result}. Check console output at ${env.BUILD_URL}"
        }
    }
}
