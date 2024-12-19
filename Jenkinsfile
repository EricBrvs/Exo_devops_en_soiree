pipeline {
    agent any

    environment {
        // Variables d'environnement, par exemple, pour Docker ou d'autres outils
    }

    stages {
        // Étape 1 : Vérifier le code source
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/EricBrvs/Exo_devops_en_soiree'
            }
        }

        // Étape 2 : Construire l'image Docker
        stage('Build Docker Image') {
            steps {
                script {
                    // Construire l'image Docker pour l'application
                    sh 'docker build -t mon-app .'
                }
            }
        }

        // Étape 3 : Lancer l'application dans un conteneur Docker
        stage('Run Application') {
            steps {
                script {
                    // Lancer le conteneur Docker
                    sh 'docker run -d -p 8080:80 --name webapp-container mon-app'
                }
            }
        }

        // Étape 4 : Test de l'application (par exemple, vérifier que le serveur est accessible)
        stage('Test Application') {
            steps {
                script {
                    // Tu peux ici ajouter des tests pour vérifier si ton application est en ligne
                    sh 'curl http://localhost:8080'
                }
            }
        }

        // Étape 5 : Nettoyer les conteneurs Docker après le pipeline
        stage('Cleanup') {
            steps {
                script {
                    sh 'docker stop webapp-container || true && docker rm webapp-container || true'
                }
            }
        }
    }
}
