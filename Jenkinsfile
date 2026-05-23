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
        stage('Run Tests') {
        parallel {
           stage('Test Add and Subtract') {
              steps {
                sh 'python3 -m pytest test_app.py::test_add test_app.py::test_subtract -v'
              }
           }
        stage('Test Multiply') {
            steps {
                sh 'python3 -m pytest test_app.py::test_multiply -v'
            }
        }
        }
}
    
    stage('Package') {
        steps {
            sh 'zip -r app.zip app.py test_app.py'
            archiveArtifacts artifacts: 'app.zip', fingerprint: true
        }
    }

    stage('Approval') {
       steps {
          input message: 'App is packaged and tests passed. Approve deployment?', ok: 'Deploy'
       }
    }

    stage('Deploy') {
       steps {
          sh 'mkdir -p /var/jenkins_home/deployments'
          sh 'cp app.zip /var/jenkins_home/deployments/'
          echo 'App successfully deployed!'
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
