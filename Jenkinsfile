// deploy on heroku
pipeline {
    agent any

    environment {
        HEROKU_APP_NAME = "joke-app-fantin"
        HEROKU_API_KEY = credentials('heroku-api-key')
    }
    stages {
        stage('Build') {
            steps {
                sh 'pnpm install'
                sh 'pnpm run test'
                sh 'pnpm run build'
            }
        },
        stage('Deploy') {
            steps {
                sh 'heroku container:login'
                sh 'heroku container:push web --app $HEROKU_APP_NAME'
                sh 'heroku container:release web --app $HEROKU_APP_NAME'
            }
        }
    }
}