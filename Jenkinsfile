pipeline {
    agent any 

    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/Sdysmore/PES2UG22CS023_JENKINS_CCLAB.git']]
                ])
            }
        }

        stage('Build') {
            steps {
                build 'PES2UG22CS023-1'
                sh 'g++ main/hello.cpp -o output'  // Intentional error: Missing semicolon in hello.cpp
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
