pipeline {
    agent any
    stages {
        stage('Debug') {
            steps {
                sh 'env'
                sh 'which docker'
                sh 'docker --version'
                sh 'docker info'
                sh 'docker run --rm busybox nslookup google.com'
            }
        }
        stage('Build') {
            steps {
                sh 'docker pull composer:latest'
                sh 'docker inspect -f . composer:latest'
                sh 'docker run composer:latest composer install'
            }
        }
        stage('Test') {
            steps {
                sh 'docker run composer:latest ./vendor/bin/phpunit tests'
            }
        }
    }
}
