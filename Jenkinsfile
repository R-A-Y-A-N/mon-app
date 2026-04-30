pipeline {
    agent any

    environment {
        DEPLOY_DIR = "C:\\deploy\\mon-app"
    }

    stages {

        stage('Clone Repo') {
            steps {
                echo '📥 Clonage du projet depuis GitHub...'
                git branch: 'main',
                    url: 'https://github.com/TON-USER/TON-REPO.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo '📦 Installation des dépendances...'
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo '🔨 Build du projet...'
                bat 'npm run build'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Exécution des tests...'
                bat 'npm test'
            }
        }

        stage('Prepare Deploy Folder') {
            steps {
                echo '📁 Préparation du dossier de déploiement...'
                bat """
                if not exist %DEPLOY_DIR% mkdir %DEPLOY_DIR%
                """
            }
        }

        stage('Deploy Local') {
            steps {
                echo '🚀 Déploiement sur machine locale...'
                bat """
                xcopy /E /Y /I build %DEPLOY_DIR%
                """
            }
        }

        stage('Run App') {
            steps {
                echo '▶ Lancement de l’application...'
                bat """
                cd %DEPLOY_DIR%
                start cmd /k node app.js
                """
            }
        }
    }

    post {
        success {
            echo '✅ Déploiement réussi sur machine locale'
        }
        failure {
            echo '❌ Échec du pipeline'
        }
        always {
            echo '🏁 Pipeline terminé'
        }
    }
}
