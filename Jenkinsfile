pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/MANEESH-KR-Y/sample_proj.git'
            }
        }

        stage('Build') {
            steps {
                dir('sample_proj') {
                    echo "Compiling main source code"
                    bat 'mvn clean compile'
                }
            }
        }

        stage('Test') {
            steps {
                dir('sample_proj') {
                    echo "Running unit tests"
                    bat 'mvn test'
                }
            }
        }

        stage('Package') {
            steps {
                dir('sample_proj') {
                    echo "Creating package"
                    bat 'mvn package'
                }
            }
        }
    }

    post {
        success {
            echo 'Build Successful'
        }
        failure {
            echo 'Build Failed'
        }
        always {
            junit 'sample_proj\\target\\surefire-reports\\*.xml'
        }
    }
}
