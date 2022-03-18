pipeline {
    agent any
    tools {
        go 'go-1.18'
    }
    environment {
        SCANNER_HOME= tool 'sonar'
        GO118MODULE = 'on'
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
		    
		    dir(path: 'cidr_convert_api/go/'){   
		    sh '''
			go version
			
			go get github.com/karmakaze/goop \\
			go get github.com/gorilla/mux \\
			go get github.com/stretchr/testify/assert \\
			go test convert.go convert_test.go 
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
