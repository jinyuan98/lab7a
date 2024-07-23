pipeline {
    agent {
        docker {
            image 'composer:latest'
        }
    }
    stages {
        stage('Debug') {
            steps {
                sh 'env'
                sh 'which docker'
                sh 'docker --version'
            }
        }
        stage('Build') {
            steps {
                sh 'composer install'
            }
        }
        stage('Test') {
            steps {
                sh './vendor/bin/phpunit tests'
            }
        }
    }
}
