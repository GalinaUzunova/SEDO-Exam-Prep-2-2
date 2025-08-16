pipeline {
    agent any

   

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Restore dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build --configuration Release'
            }
        }

        stage('Unit Tests') {
            steps {
                bat 'dotnet test  --configuration Release --no-build'
            }
        }

        stage('Integration Tests') {
            steps {
                bat 'dotnet test tests/IntegrationTests/IntegrationTests.csproj --configuration Release --no-build'
            }
        }
    }

   
}
