pipeline {
    agent any
    environment {
        SECRET_VAR = credentials('secret_text')
    }
    stages{
        stage('prep') {
            steps {
                sh 'chmod +x ./cleanup.sh'
                sh './cleanup.sh'
            }
        }
        stage('build image') {
            steps {
                sh 'docker build -t nginx-image .'
            }
        }
        stage('run container') {
            steps {
                sh 'docker run -d --name nginx-container -p 80:80 nginx-image'
                sh 'echo $SECRET_VAR'
            }
        }
    }
}
