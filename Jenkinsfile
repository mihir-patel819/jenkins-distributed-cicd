
pipeline {
    agent {
        label 'worker'
    }

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Downloading website from GitHub'

                git branch: 'main',
                    url: 'https://github.com/mihir-patel819/jenkins-distributed-cicd.git'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website using Jenkins Worker'

                sh '''
                    cp -r website/. /var/www/jenkins-site/
                    chmod -R 755 /var/www/jenkins-site/
                '''
            }
        }

        stage('Verify') {
            steps {
                sh 'curl -f http://localhost'
                echo 'Website deployment successful!'
            }
        }
    }
}
