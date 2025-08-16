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
                bat 'dotnet test tests/UnitTests/UnitTests.csproj --configuration Release --no-build'
            }
        }

        stage('Integration Tests') {
            steps {
                bat 'dotnet test tests/IntegrationTests/IntegrationTests.csproj --configuration Release --no-build'
            }
        }
    }

    post {
        always {
            junit '**/TestResults/*.xml' // Publish test results
        }
        failure {
            mail to: 'team@example.com',
                 subject: "❌ Build Failed in Jenkins: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                 body: "Check Jenkins for details: ${env.BUILD_URL}"
        }
    }
}
