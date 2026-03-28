pipeline {
    agent any
    stages {
        stage('Custom Checkout') {
            dir('/Users/pratibhapandey/Personal/PyProjects/devops/workspace'){checkout scmGit(
                 branches: [[name: 'main']],
                 userRemoteConfigs: [[credentialsId: 'GITHUB_TOKEN2',
                 url: 'https://github.com/kunaldey88/testing-fast-api.git']])
        }}
    }
}
