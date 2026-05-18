pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ambrin64/devops_assignment.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm.cmd install'
            }
        }

        stage('Run SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    bat '''
                    sonar-scanner ^
                    -Dsonar.projectKey=devops_assignment ^
                    -Dsonar.sources=. ^
                    -Dsonar.host.url=http://localhost:9000 ^
                    -Dsonar.login=squ_15bb93a8be009f9fbd172b3de3c23fb83bc1f32b
                    '''
                }
            }
        }
    }
}