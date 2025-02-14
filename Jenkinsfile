pipeline {
    agent any
    environment {
        SERVER_IP = '192.168.0.39'
        DEPLOY_DIR = '/opt/stacks/jenkins'
        CREDENTIALS_ID = 'home-intranet-server-ssh'
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/Lanham-Software-James/Home-Intranet-Jenkins.git'
            }
        }

        stage('Copy Files to Server') {
            steps {
                sshagent(credentials: [CREDENTIALS_ID]) {
                    sh "scp -o StrictHostKeyChecking=no docker-compose.yml ${SERVER_IP}:${DEPLOY_DIR}/docker-compose.yml"
                }
            }
        }
    }
}
