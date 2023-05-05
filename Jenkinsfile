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
            environment {
                SCANNER_HOME = tool 'SonarQube Scanner'
                PROJECT_KEY = 'jenkins-nude'
            }
            steps {
                echo '*** Scanning the code...'
                // test command here
                withSonarQubeEnv('SonarQube server') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner \
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
