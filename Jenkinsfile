pipeline {
    agent any
    tools { go '1.20' }
    stages {
        stage('Build') {
            steps {
                echo "step build"
                echo 'test trigger webhook 3'
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