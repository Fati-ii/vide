pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Fati-ii/vide.git'
            }
        }

        stage('Build + Sonar') {
            steps {
                withSonarQubeEnv('sonarScanner') {
                    bat "mvn clean verify sonar:sonar -Dsonar.projectKey=com.ops:devops -Dsonar.projectName=com.ops:devops -Dsonar.host.url=http://localhost:9000 -Dsonar.token=sqp_ff05561c7f3e0f3280b72892726b3fb6b6b32dae"
                }
            }
        }
    }
}
