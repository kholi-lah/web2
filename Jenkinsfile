pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/USERNAME/muk2-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t muk2-app .'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Running dummy tests..."'
                sh 'test -f index.html'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f muk2-container || true
                docker run -d --name muk2-container -p 80:80 muk2-app
                '''
            }
        }
    }
}
