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
                    // Build the Docker image and store its name in dockerImage
                    dockerImage = docker.build("${registry}:${BUILD_NUMBER}")
                }
            }
        }

        stage('Run Docker Container') {
            agent any
            steps {
                script {
                    // Run the container with the correct image reference
                    sh "docker run -d --name ml_model_container ${dockerImage.imageName()}"
                }
            }
        }
    }
}
