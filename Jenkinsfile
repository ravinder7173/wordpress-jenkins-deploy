pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ravinder7173/wordpress-jenkins-deploy.git'
            }
        }

        stage('Build & Deploy') {
            steps {
                sh 'docker-compose down || true'
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        success {
            echo "🎉 WordPress deployed successfully at http://<EC2_PUBLIC_IP>:8080"
        }
        failure {
            echo "❌ Deployment failed. Check logs."
        }
    }
}

