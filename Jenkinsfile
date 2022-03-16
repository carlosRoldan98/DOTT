pipeline {
    agent any
    environment {
    SCANNER_HOME= tool 'sonar'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building.....'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing.....'
                withSonarQubeEnv('sonar') { 
                    sh''' 
                    cd ./cidr_convert_api/go
                    ${SCANNER_HOME}/bin/sonar-scanner \
                        -Dsonar.organization=carlosroldan98 \
                        -Dsonar.projectKey=carlosRoldan98_DOTT \
                        -Dsonar.sources=./cidr_convert_api/go \
                        -Dsonar.host.url=https://sonarcloud.io
                        '''
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying.....'
            }
        }
    }
}
