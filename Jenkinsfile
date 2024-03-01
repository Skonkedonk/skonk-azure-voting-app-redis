pipeline {
    agent any

    environment {
        GIT_CREDENTIAL_ID = 'skonk-fork-pat'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                userRemoteConfigs: [[credentialsId: env.GIT_CREDENTIAL_ID, url: 'https://github.com/Skonkedonk/skonk-azure-voting-app-redis.git']]])
            }
        }    
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Docker Build') {
            steps {
                sh(script: 'docker compose build')
            }
        }
    }
    
}