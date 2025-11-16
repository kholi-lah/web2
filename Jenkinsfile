pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kholi-lah/web2.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t muk2-app .'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Running basic test..."'
                sh 'test -f index.html'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                    docker rm -f muk2-container || true
                    docker run -d --name muk2-container -p 80:80 muk2-app
                '''
            }
        }
    }
}
