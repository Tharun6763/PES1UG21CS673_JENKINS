pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/Tharun6763/PES1UG21CS673_Jenkins']]])
            }
        }
        stage('Build') {
            steps {
                // Ensure that 'PES1UG21CS673-1' is the correct job name in Jenkins
                build job: 'PES1UG21CS673-1'
                sh 'g++ working.cpp -o output'
            }
        }
        stage('Test') {
            steps {
                sh './output'
            }
        }
        stage('Deploy') {
            steps {
                echo 'deploy'
            }
        }
    }

    post {
        failure {
            error 'Pipeline failed'
        }
    }
}
