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
//                 dependencyCheck additionalArguments: '''
//                    -o "./"
//                    -s "./"
//                    -f "ALL"
//                    --prettyPrint''',
//                        odcInstallation: 'SCA: Dependency-Check'
//                 dependencyCheckPublisher pattern: 'dependency-check-report.xml'
            }
        }
        stage('SAST') {
            steps {
                echo '*** Scanning the code...'
                // test command here
                environment {
                    SCANNER_HOME = tool 'SonarQube Scanner'
                    $PROJECT_KEY = 'jenkins-nude'
                }
                withSonarQubeEnv('SonarQube server') {
                    sh '''${scannerHome}/bin/linux-x86-64/sonar.sh \
                    -Dsonar.projectKey=$PROJECT_KEY \
                    -Dsonar.projectName='Java project analyzed by SonarQube' \
                    -Dsonar.projectVersion=1.0 \
                    -Dsonar.sources=. \
                    -Dsonar.language=java \
                    -Dsonar.sourceEncoding=UTF-8 \
                    -Dsonar.java.binaries=.
                    '''
                }
            }
        }
        stage('Deploy') {
            steps {
                echo '*** Deploying the project...'
                // deploy command here
            }
        }
    }
}
