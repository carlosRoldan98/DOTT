pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building.....'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing.....'
                sh''' 
                cd ./cidr_convert/go
                sonar-scanner \
                    -Dsonar.organization=carlosroldan98 \
                    -Dsonar.projectKey=carlosRoldan98_DOTT \
                    -Dsonar.sources=. \./cidr_convert/go
                    -Dsonar.host.url=https://sonarcloud.io
                    '''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying.....'
            }
        }
    }
}
