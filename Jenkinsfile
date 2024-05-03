pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Step 1: Building application by Gradle"
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo "Step 2: Run unit and integrate tests with Unit and Testing"
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Step 3: Analyzing the code using a static code analysis tool"
            }
        }

        stage('Security Scan') {
            steps {
                echo "Step 4: Performing a security scan using OWASP ZAP"
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Step 5: Deploying the application to a staging server on AWS"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Step 6: Executing integration tests on the staging environment"
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Step 7: Deploying the application to a production server on Azure"
            }
        }
    }

    post {
        success {
            echo "Pipeline execution succeeded!"
            emailext(
                to: "nssuryasubramanya@gmail.com",
                subject: "Pipeline Status: Success",
                body: "The Jenkins pipeline has successfully completed all tasks.",
                attachLog: true
            )
        }
        failure {
            echo "nssuryasubramanya@gmail.com"
            emailext(
                to: "nssuryasubramanya@gmail.com",
                subject: "Pipeline Status: Failure",
                body: "The Jenkins pipeline has encountered issues and failed. Please review the logs for details.",
                attachLog: true
            )
        }
    }
}
