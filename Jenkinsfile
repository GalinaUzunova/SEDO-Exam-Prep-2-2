pipeline {
    agent any

  

    stages {
        stage('Checkout repository') {
            steps {
                checkout scm
            }
        }
        
        stage('Restore dependency') {
          
            steps {
                bat 'dotnet restore'
            }
        }
        
        stage('Build') {
           
            steps {
                bat 'dotnet build --configuration Release'
            }
        }
        
        stage('Test Unit Test') {
           
            steps {
                bat 'dotnet test --configuration Release --no-build'
            }
        }
      stage('Integration Tests') {
            steps {
                bat "dotnet test --configuration Release --no-build --filter \"Category=Integration\" --logger \"trx;LogFileName=integration-tests.trx\""
    }

      }
}
