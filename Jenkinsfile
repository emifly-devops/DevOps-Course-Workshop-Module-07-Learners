pipeline {
    agent none
    environment {
        DOTNET_CLI_HOME = "/tmp/DOTNET_CLI_HOME"
        XDG_DATA_HOME = "/tmp/XDG_DATA_HOME"
    }
    stages {
        stage('.NET build and test') {
            agent {
                docker { image 'mcr.microsoft.com/dotnet/sdk:6.0' }
            }
            steps {
                sh 'dotnet build'
                sh 'dotnet test'
            }
        }
        stage('Typescript build and test') {
            agent {
                docker { image 'node:alpine' }
            }
            steps {
                dir('DotnetTemplate.Web') {
                    sh 'npm install'
                    sh 'npm run build'
                    sh 'npm run lint'
                    sh 'npm run test'
                }
            }
        }
    }
}
