
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Regression Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Report') {
            steps {
                junit 'target/surefire-reports/*.xml'
                echo 'Regression testing passed!'
            }
        }
    }

    post {
        success {
            echo 'Regression testing passed!'
        }
        failure {
            echo 'Regression testing failed!'
        }
    }
}
