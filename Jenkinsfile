pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo '*** Building the project...'
                // build command here
                sh 'javac Main.java'
            }
        }
        stage('SCA') {
            steps {
                echo '*** Checking libraries...'
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
        stage('SAST') {
            steps {
                echo '*** Scanning the code...'
                // test command here
                script {
                    scannerHome = tool 'SonarQube Scanner';
                }
                withSonarQubeEnv('SonarQube Scanner') {
                    sh "${scannerHome}/bin/linux-x86-64/sonar.sh" 
                }
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
