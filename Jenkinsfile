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
                echo 'CI validation successful'
            }
        }

        stage('Build') {
            steps {
                echo 'Building ShopKart application'
                sh 'ls -la'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying ShopKart to Nginx'
                sh 'sudo cp index.html /var/www/html/index.html'
                echo 'Deployment completed successfully'
            }
        }
    }

    post {
        success {
            echo 'ShopKart CI/CD Pipeline completed successfully'
        }

        failure {
            echo 'ShopKart CI/CD Pipeline failed'
        }
    }
}
