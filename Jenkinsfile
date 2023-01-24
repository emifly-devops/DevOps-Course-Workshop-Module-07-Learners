pipeline {
    agent none
    stages {
        stage('.NET build and test') {
            agent {
                docker { image 'mcr.microsoft.com/dotnet/sdk:6.0' }
            }
            steps {
                sh 'dotnet build'
                sh 'dotnet run'
            }
        }
        stage('Typescript build and test') {
            agent {
                docker { image 'node:alpine' }
            }
            steps {
                sh 'cd DotnetTemplate.Web'
                sh 'npm install'
                sh 'npm run build'
                sh 'npm run lint'
                sh 'npm run test'
            }
        }
    }
}
