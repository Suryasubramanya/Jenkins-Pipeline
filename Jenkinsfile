stage('Deploy to Production') {
    steps {
        // Deploy the application to a production server using Docker
        sh 'docker build -t my-app:v1.0 .'
        sh 'start /b docker run -d -p 80:8080 my-app:v1.0'
    }
}
