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
                    sh '''
                        CONTAINER_IDS=$(docker ps -aq)
                        if [ ! -z "$CONTAINER_IDS" ]; then
                            docker rm -f $CONTAINER_IDS
                        fi
                    '''
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