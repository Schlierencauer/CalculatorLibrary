pipeline{
    agent {
        docker { image 'public.ecr.aws/docker/library/python:latest'
                 //label 'android-aws'
         }
    }
    stages {
        stage('Source') {
            steps{
                git branch: 'main',
                    url: 'https://github.com/Schlierencauer/CalculatorLibrary.git'
            }
        }
        stage('Setup') {
            steps{
                sh ("python3 -m venv venv")
                sh (". venv/bin/activate")
                sh ("sudo pip install -r requirements.txt")
            }
        }
        stage('Test') {
            steps{
                sh ("pytest -v --cov")
            }
        }
    }
}
