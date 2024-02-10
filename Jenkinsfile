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
                sh 'scp -o StrictHostKeyChecking=no -i $RSA_TRAINER myapp trainer@34.101.120.65:~'
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
            }
        }
    }
}