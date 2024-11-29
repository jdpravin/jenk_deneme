pipeline {
    environment {
        registry = 'jenk_deneme/ml_model'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Build Docker Image') {
            agent any
            steps {
                script {
                    sh 'sudo chmod 666 /var/run/docker.sock'
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
        stage('Run Docker Container') {
            agent any
            steps {
                script {
                    // Run the built Docker container
                    sh "docker run -d --name ml_model_container ${dockerImage}"
                }
            }
        }
    }
}
