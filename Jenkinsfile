pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/feshal117/juice-shop-devsecops.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh '''
                    /usr/bin/sonar-scanner \
                      -Dsonar.projectKey=juice-shop \
                      -Dsonar.sources=. \
                      -Dsonar.host.url=http://sonarqube:9000 \
                      -Dsonar.login=sqa_182da32337956fe7cd80fc0bb1c70abdabaf4c65
                    '''
                }
            }
        }
    }
}
