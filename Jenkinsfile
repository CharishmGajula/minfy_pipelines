pipeline {
    agent any

        environment {
        DOCKERHUB_CREDENTIALS = 'dockerhub-credentials' 
        IMAGE_NAME = 'charishmagajula/minfy-python-demo-main'
    }

    stages
    {
        stage("ls"){
            steps{
                sh 'ls'
            }
        }
        stage("Build Docker Image") {
            steps {
                echo "Building Docker image: ${IMAGE_NAME}"
                sh "docker build -t ${IMAGE_NAME} ."
            }
        }
        stage("Run the image")
        {
            steps{
                sh 'docker run --rm minfy-python-demo-main'
            }
        }
        stage('Push to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: "${DOCKERHUB_CREDENTIALS}", usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    sh 'docker push ${IMAGE_NAME}'
                }
            }
        }
    
    }
    post{
        always
        {
            sh 'docker logout'
        }
    }
}