pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/fredericEducentre/landing-page-example.git'
            }
        }

        stage('Déploiement sur AlwaysData') {
            steps {
                withCredentials([string(credentialsId: 'alwaysdata-password', variable: 'PASSWORD')]) {
                    sh """
                        echo "Déploiement en cours..."
                        sshpass -p "$PASSWORD" scp -o StrictHostKeyChecking=no -p ./index.html \
                        thanus@ssh-thanus.alwaysdata.net:/home/thanus/www/index.html
                        echo "Déploiement terminé !"
                    """
                }
            }
        }

        stage('Success') { 
            steps { 
                echo 'Success' 
            } 
        }
    }
}
