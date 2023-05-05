pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo '***************************'
                echo '*** Building the project...'
                echo '***************************'
                // build command here
                sh 'javac Main.java'
            }
        stage('Test') {
            steps {
                echo '***************************'
                echo '*** Testing the project...'
                echo '***************************'
                // test command here
            }
        }
        stage('Deploy') {
            steps {
                echo '***************************'
                echo '*** Deploying the project...'
                echo '***************************'
                // deploy command here
            }
        }
    }
}
