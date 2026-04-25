pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo '=== Etape 1 : Build ==='
                script {
                    if (isUnix()) {
                        sh 'cat README.md'
                    } else {
                        bat 'type README.md'
                    }
                }
            }
        }

        stage('Debug Test') {
            steps {
                bat 'type test.js'
            }
        }

        stage('Test') {
            steps {
                echo '=== Etape 2 : Test ==='
                script {
                    if (isUnix()) {
                        sh 'node test.js'
                    } else {
                        bat 'node test.js || exit 1'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo '=== Etape 3 : Deploy ==='
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