pipeline {
    agent any
    tools { go '1.20' }
    environment {
        RSA_TRAINER = credentials('rsa-trainer')
    }
    stages {
        stage('Build') {
            steps {
                echo "step build"
                sh 'go build -o myapp'
                
            }
        }
        stage('Test') {
            steps {
                echo "step test"
            }
        }
        stage('Deploy') {
            steps {
                echo "step deploy"
                sh 'ssh -o StrictHostKeyChecking=no -i $RSA_TRAINER trainer@34.101.120.65 "sudo systemctl stop marketplace"'
                sh 'scp -o StrictHostKeyChecking=no -i $RSA_TRAINER myapp trainer@34.101.120.65:~'
                sh 'ssh -o StrictHostKeyChecking=no -i $RSA_TRAINER trainer@34.101.120.65 "sudo systemctl start marketplace"'
            }
        }
    }
    post {
        success {
            discordSend description: "Jenkins Pipeline", footer: "Deploy Marketplace", link: env.BUILD_URL, result: currentBuild.currentResult, title: JOB_NAME, webhookURL: "https://discord.com/api/webhooks/1205721470731550760/lc2EspOhjl_cKmLJWY2AcdYW1Qia1LGkGPle82ON0QWNPPZH7aEeZJdY59qCf1SHOYEX"
        }
    }
}