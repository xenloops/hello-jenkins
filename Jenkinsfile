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
        }
        stage('SCA') {
            steps {
                echo '***************************'
                echo '*** Testing the project...'
                echo '***************************'
                // SCA command here
                dependencyCheck additionalArguments: '''
                   -o "./"
                   -s "./"
                   -f "ALL"
                   --prettyPrint''',
                       odcInstallation: 'SCA: Dependency-Check'
                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
            }
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
