pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo '=== Etape 1 : Build ==='
                echo 'Compilation du projet en cours...'
                
                // Compatible Windows + Linux
                script {
                    if (isUnix()) {
                        sh 'cat README.md'
                    } else {
                        bat 'type README.md'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                echo '=== Etape 2 : Test ==='
                echo 'Execution des tests...'

                script {
                    if (isUnix()) {
                        sh 'node test.js'
                    } else {
                        bat 'node test.js'
                    }
                }
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
    stage('Debug Test') {
    steps {
        bat 'type test.js'
    }
}
}
