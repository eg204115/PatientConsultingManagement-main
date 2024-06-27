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
                        CONTAINER_IDS=$(sudo docker ps -aq)
                        if [ ! -z "$CONTAINER_IDS" ]; then
                            sudo docker stop $CONTAINER_IDS || true
                            sudo docker rm -f $CONTAINER_IDS || true
                        fi
                    '''

                    sh 'sudo docker-compose up -d --build'
                }
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}
