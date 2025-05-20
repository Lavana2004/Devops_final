pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "consultancy_app_image"
        CONTAINER_NAME = "consultancy_app_container"
        APP_PORT = "5173"
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out code...'
                git url: 'https://github.com/Lavana2004/Devops_final.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dir('consultancy_final_draft/project-2') {
                        echo "Building Docker image: ${DOCKER_IMAGE}"
                        bat "docker build -t %DOCKER_IMAGE% ."
                    }
                }
            }
        }

        stage('Stop Existing Container (if any)') {
            steps {
                script {
                    echo "Stopping and removing existing container if it exists..."
                    bat """
                        docker stop %CONTAINER_NAME% || exit 0
                        docker rm %CONTAINER_NAME% || exit 0
                    """
                }
            }
        }

        stage('Deploy New Container') {
            steps {
                script {
                    echo "Deploying new container: ${CONTAINER_NAME}"
                    bat "docker run -d --name %CONTAINER_NAME% -p %APP_PORT%:%APP_PORT% %DOCKER_IMAGE%"
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished execution.'
        }
        success {
            echo '✅ Deployment successful!'
        }
        failure {
            echo '❌ Deployment failed!'
        }
    }
}
