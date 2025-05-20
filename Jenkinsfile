pipeline {
    agent any
    stages
    {
        stage("ls"){
            steps{
                sh 'ls'
            }
        }
        stage("Build the image")
        {
            steps{
                sh 'docker build -t minfy-python-demo-main .'
            }
        }
        stage("Run the image")
        {
            steps{
                sh 'docker run --rm minfy-python-demo-main'
            }
        }
    }
}