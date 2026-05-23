pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'pip3 install pytest --break-system-packages'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'python3 -m pytest test_app.py -v'
            }
        }
    
    stage('Package') {
        steps {
            sh 'zip -r app.zip app.py test_app.py'
            archiveArtifacts artifacts: 'app.zip', fingerprint: true
        }
    }
    }

    post {
        success {
            echo 'All tests passed!'
        }
        failure {
            echo 'Some tests failed. Check the console output.'
        }
    }
}
