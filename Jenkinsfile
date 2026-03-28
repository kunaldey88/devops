pipeline {
    agent any
    stages {
        stage('Custom Checkout') {
            steps {
                dir('/Users/pratibhapandey/Personal/PyProjects/jenkins-workspace') {
                checkout scmGit(
                    branches: [[name: 'main']],
                    userRemoteConfigs: [[credentialsId: 'GITHUB_TOKEN2',
                    url: 'https://github.com/kunaldey88/testing-fast-api.git']],
                    extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'git-plugin-repo']] )
                }
            }
            
        }
    }
}
