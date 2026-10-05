pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out ShopKart source code'
            }
        }

        stage('CI Validation') {
            steps {
                echo 'Validating ShopKart application'
                sh 'test -f index.html'
                sh 'test -f Dockerfile'
                echo 'CI validation successful'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building ShopKart Docker image'
                sh 'docker build -t shopkart:1.0 .'
            }
        }

        stage('Docker Deploy') {
            steps {
                echo 'Deploying ShopKart Docker container'

                sh '''
                    docker stop shopkart-container || true
                    docker rm shopkart-container || true
                    docker run -d --name shopkart-container -p 8081:80 shopkart:1.0
                '''

                echo 'ShopKart Docker deployment completed successfully'
            }
        }
    }

    post {
        success {
            echo 'ShopKart Docker CI/CD Pipeline completed successfully'
        }

        failure {
            echo 'ShopKart Docker CI/CD Pipeline failed'
        }
    }
}
