pipeline {
    agent any
    environment {
        REGISTRY = '554358105146.dkr.ecr.us-east-1.amazonaws.com/py-app-containers'
        REGISTRY_CREDENTIALS_ID = 'AWS_CREDS_1'
        DOCKER_IMAGE = ''
    }
    stages {
        stage('Custom Checkout') {
            steps {
                dir('/Users/pratibhapandey/Personal/PyProjects/jenkins-workspace') {
                    checkout scmGit(
                    branches: [[name: 'main']],
                    userRemoteConfigs: [[credentialsId: 'GITHUB_TOKEN2',
                    url: 'https://github.com/kunaldey88/testing-fast-api.git']]
                    )
                }
            }
        }

        stage('Build Image') {
            steps {
                script {
                    dockerImage = docker.build $REGISTRY + ":$BUILD_NUMBER"
                }
            }
        }

        stage('Deploy image') {
        steps{
            script{
                docker.withRegistry("https://" + $REGISTRY, "ecr:us-east-1:" + $REGISTRY_CREDENTIALS_ID) {
                    dockerImage.push()
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
