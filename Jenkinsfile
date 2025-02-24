pipeline {
    agent any
    environment {
        USER = 'jenkins'
        SERVER_IP = 'home-intranet'
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
                    sh "scp -o StrictHostKeyChecking=no docker-compose.yml ${USER}@${SERVER_IP}:${DEPLOY_DIR}/docker-compose.yml"
                }
            }
        }
    }
}
