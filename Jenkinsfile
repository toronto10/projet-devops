pipeline {
    agent any

    stages {
        stage('Récupérer le code') {
            steps {
                echo 'Clonage du repo GitHub...'
                checkout scm
            }
        }

        stage('Construire image Docker') {
            steps {
                echo 'Construction de l image Docker...'
                sh 'docker build -t projet-devops:latest .'
            }
        }

        stage('Lancer le conteneur') {
            steps {
                echo 'Lancement de l application...'
                sh 'docker run -d -p 5000:5000 --name mon-app projet-devops:latest'
            }
        }
    }

    post {
        success {
            echo 'Pipeline terminé avec succès ! ✅'
        }
        failure {
            echo 'Quelque chose a échoué ❌'
        }
    }
}