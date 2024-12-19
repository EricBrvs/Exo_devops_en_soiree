pipeline {
    agent any

    environment {
        PATH = "/usr/local/bin:$PATH"  // Ajoute Docker au PATH
    }

    stages {
        stage('Checkout code') {
            steps {
                git branch: 'main', url: 'https://github.com/EricBrvs/Exo_devops_en_soiree'
            }
        }

        stage('Build docker image') {
            steps {
                sh 'docker build -t webapp-apache .'
            }
        }

        stage('Provision instance') {
            steps {
                sh 'docker run -d -p 8080:80 --name webapp-container webapp-apache'
            }
        }

        stage('Deploy instance') {
            echo 'Application successfully deployed on http://localhost:8080'
        }
    }
}
