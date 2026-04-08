pipeline {
    agent any

    tools {
        maven 'maven 3.9.14' 
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/MANEESH-KR-Y/sample_proj.git'
            }
        }

        stage('Build') {
            steps {
                echo "Compiling main source code"
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo "Running unit tests"
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo "Creating package"
                bat 'mvn package'
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
            junit 'target/surefire-reports/*.xml', allowEmptyResults: true
        }
    }
}