pipeline {
    environment {
        registry = 'jenk_deneme/ml_model'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'sudo chmod 666 /var/run/docker.sock'
                    // Build the Docker image and store its name in dockerImage
                    dockerImage = docker.build("${registry}:${BUILD_NUMBER}")
                }
            }
        }

        stage('Run and Stop Docker Container') {
            steps {
                script {
                    // Run the container in detached mode
                    sh "docker run -d --name ml_model_container ${dockerImage.imageName()}"
                    
                    // Add your additional container setup here (if needed)
                    // For example, wait for the container to complete some task
                    // sleep(10) // Uncomment if needed

                    // Stop and remove the container immediately after running
                    sh "docker stop ml_model_container"
                    sh "docker rm ml_model_container"
                }
            }
        }
    }
}
