pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage('Checkout') {
            steps {
                // Note: En environnement Jenkins réel, le checkout est automatique si le Jenkinsfile est dans le repo.
                // Ici je garde votre structure mais adaptée au projet actuel.
                checkout scm
            }
        }

        stage('Build + Sonar') {
            steps {
                // Utilise le nom de l'environnement SonarQube configuré dans Jenkins
                withSonarQubeEnv('sonarScanner') {
                    // Utilise 'bat' car vous êtes sur Windows
                    bat 'mvn clean verify sonar:sonar'
                }
            }
        }
    }
}
