pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                sh 'mvn sonar:sonar'
            }
        }

        stage('Security Scan') {
            steps {
                sh 'snyk test'
            }
        }

        stage('Deploy to Staging') {
            steps {
                sh 'ansible-playbook staging-playbook.yml'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                sh 'mvn verify -P staging'
            }
        }

        stage('Deploy to Production') {
            steps {
                sh 'ansible-playbook production-playbook.yml'
            }
        }
    }

    post {
        always {
            emailext subject: 'Jenkins Pipeline Report',
                      body: 'See attached logs for pipeline status.',
                      attachLog: true,
                      to: 's223113345@deakin.edu.au'
        }
    }
}