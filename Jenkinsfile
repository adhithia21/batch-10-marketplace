pipeline {
    agent any
    tools { go '1.20' }
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
            }
        }
    }
}