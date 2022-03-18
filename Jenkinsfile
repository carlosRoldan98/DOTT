pipeline {
    agent any
    tools {
        go 'go-1.10'
    }
    environment {
        SCANNER_HOME= tool 'sonar'
        GO110MODULE = 'on'
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
                        -Dsonar.sources=. \
                        -Dsonar.host.url=https://sonarcloud.io
                        '''
                }
            }
        }
        stage('Unit Test'){
            steps {
                echo 'Unit testing'
             sh '''
	     	go version
		cd ./cidr_convert_api/go/
                go get github.com/Pepegasca/goop
                go test 
                
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
