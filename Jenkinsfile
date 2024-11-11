pipeline { 
    agent any
    stages {
        stage('Cleanup') {
            steps {
                sh 'rm -rf target'
            }
        }
        stage('Checkout') {
            steps {
                git 'https://github.com/Halcyon757/JenkinsTest.git'
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
        stage('Deploy') {
            steps {
                sh 'sudo cp target/demo-project-1.0-SNAPSHOT.war /var/lib/jetty9/webapps/ROOT.war'
                sh 'sudo systemctl restart jetty9'
            }
        }
    }
}
