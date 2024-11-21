pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Installing dependencies...'
                sh '''
                python -m pip install --upgrade pip
                python -m pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'python -m unittest discover -s .'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh '''
                mkdir -p /tmp/python-app-deploy
                cp app.py /tmp/python-app-deploy/
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for more details.'
        }
    }
}

