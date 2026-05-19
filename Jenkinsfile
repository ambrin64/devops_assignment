pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ambrin64/devops_assignment.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '"C:\\Program Files\\nodejs\\npm.cmd" install'
            }
        }

        stage('Run SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    bat 'sonar-scanner -Dsonar.projectKey=devops_assignment -Dsonar.sources=. -Dsonar.host.url=http://localhost:9000'
                }
            }
        }
    }
}