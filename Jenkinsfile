pipeline {
    agent any
    options {
        skipDefaultCheckout()
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
                sh 'ls -la public'
            }
        }
        stage('Test') {
            steps {
                sh 'test -f public/index.html'
                sh 'grep -qi "<html" public/index.html'
                sh 'grep -qi "</html>" public/index.html'
                sh 'grep -qi "<title>" public/index.html'
            }
        }
        stage('Deploy') {
            steps {
                sh 'cp -r public/* /var/www/html/'
            }
        }
    }
}
