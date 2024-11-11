pipeline { 
    agent any
    stages {
        stage('Pre-Cleanup') {
            steps {
                // Удаление папки target с использованием sudo для получения нужных прав
                sh 'sudo rm -rf target'
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
                // Копирование .war файла в папку Jetty
                sh 'sudo cp target/demo-project-1.0-SNAPSHOT.war /var/lib/jetty9/webapps/ROOT.war'
                // Перезапуск Jetty для обновления развернутого приложения
                sh 'sudo systemctl restart jetty9'
            }
        }
    }
}
