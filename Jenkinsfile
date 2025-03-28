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
        stage('run container') {
            steps {
                sh 'docker run -d --name nginx-container -p 80:80 nginx:latest'
                sh """
                    docker exec nginx-container sh -c 'echo "hello jenkins! ${SECRET_VAR}" > /usr/share/nginx/html/index.html'
                """
            }
        }
    }
}
