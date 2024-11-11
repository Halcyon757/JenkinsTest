pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ваш_пользователь/demo-project.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
