pipeline {
    agent any 

        stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/eg204115/PatientConsultingManagement-main.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                dir('frontend') {
                    sh 'npm install'
                }
                dir('backend') {
                    sh 'npm install'
                }
            }
        }
        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    sh 'npm run build'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'docker rm -f $(docker ps -aq)'
                    sh 'docker-compose up -d --build' 
                }
            }
        }
    }
    post {
        always {
            bat 'docker logout'
        }
    }
}