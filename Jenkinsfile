pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Клонирование репозитория с GitHub
                git 'https://github.com/username/my-sample-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Собираем Docker-образ
                script {
                    dockerImage = docker.build("my-sample-app")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                // Запуск Docker-контейнера
                script {
                    dockerImage.run('-p 3000:3000')
                }
            }
        }
    }

    post {
        always {
            // Удаление контейнера после завершения
            script {
                dockerImage.stop()
            }
        }
    }
}
