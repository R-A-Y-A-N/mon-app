pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo '=== Etape 1 : Build ==='
                echo 'Compilation du projet en cours...'
                bat 'type README.md'
            }
        }

        stage('Test') {
            steps {
                echo '=== Etape 2 : Test ==='
                echo 'Execution des tests...'
                bat 'node test.js'
            }
        }

        stage('Deploy') {
            steps {
                echo '=== Etape 3 : Deploy ==='
                echo 'Deploiement en production...'
                echo 'Application deployee avec succes !'
            }
        }
    }

    post {
        always {
            echo 'Pipeline termine !'
        }
        success {
            echo 'SUCCES : toutes les etapes sont passees'
        }
        failure {
            echo 'ECHEC : une etape a echoue'
        }
    }
} 
