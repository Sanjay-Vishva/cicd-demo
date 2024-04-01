pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Build Docker image
                    sh 'docker build -t flask-app .'
                }
            }
        }

        stage('Test') {
            steps {
                // Test app.py
                sh 'docker run --rm flask-app pytest test.py'
                
                // Test app.py itself
                script {
                    // Install pytest inside the Docker container
                    sh 'docker run --rm flask-app pip install pytest'
                    // Run tests inside the Docker container
                    sh 'docker run --rm flask-app pytest app.py'
                }
            }
        }
    }
}
