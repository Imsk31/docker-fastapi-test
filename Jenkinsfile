pipeline {
    agent {
        label 'docker-server'
    }

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Imsk31/docker-fastapi-test.git'
            }
        }
        stage('Deploy with Docker Compose') {
            steps {
                sh '''
                docker compose up -d --build
                '''
            }
        }
        stage('Verify Deployments') {
            steps {
                sh '''
                docker ps -a
                '''
            }
        }
    }
    post {
        success {
            echo 'Deployment successful'
        }
        failure {
            echo 'Pipeline failed'
        }
        // always {
        //     cleanWs()
        // }
    }
}