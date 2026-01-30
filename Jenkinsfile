pipeline {
    agent any
    
    environment {
        MVN_TAG = '3.9.5-eclipse-temurin-17'
        MVN_ARGS = ''
        MVN_CMD = 'mvn'
        MVN_CMD_ARGS = ''
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code'
                checkout scm
            }
        }
        
        stage('Build and Test') {
            steps {
                script {
                    def containerArgs = "${env.MVN_ARGS} -v /var/run/docker.sock:/var/run/docker.sock"
                    
                    docker.image("maven:${env.MVN_TAG}").inside(containerArgs) {
                        echo 'Executing unit tests with coverage report'
                        sh "${MVN_CMD} clean verify ${MVN_CMD_ARGS}"
                    }
                }
            }
        }
    }
    
    post {
        always {
            echo 'Cleaning up workspace'
            cleanWs()
        }
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
