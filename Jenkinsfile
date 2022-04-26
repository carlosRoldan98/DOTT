pipeline {
    environment {

        SCANNER_HOME= tool 'sonarDOTT'

    }
    
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Testingggg') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Sonar') {
            steps {
                echo 'SonarCloud'
                 sh '''withSonarQubeEnv('sonarDOTT') {
                    sonar-scanner \
                        -Dsonar.organization=carlosroldan98 \
                        -Dsonar.projectKey=carlosRoldan98_DOTT \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=https://sonarcloud.io '''
                }
            }
        }
        stage('Deployingggg') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
