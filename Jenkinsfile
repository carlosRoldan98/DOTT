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
                cd ./cikdr_convert/go
                sonar-scanner \
                    -Dsonar.organization=carlosroldan98 \
                    -Dsonar.projectKey=carlosRoldan98_DOTT \
                    -Dsonar.sources=. \
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
