pipeline {
    agent any

    stages {

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
            junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
        }
    }
}