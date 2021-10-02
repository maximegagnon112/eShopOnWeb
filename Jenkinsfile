pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        pwsh 'dotnet build eShopOnWeb.snl'
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            bat 'dotnet test tests/UnitTests'
          }
        }

        stage('integration') {
          steps {
            bat 'dotnet test tests/IntegrationTests'
          }
        }

        stage('Functional') {
          steps {
            bat 'dotnet test tests/FunctionalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        bat 'dotnet publish eShopOnWeb.sln -o C:\\Users\\gagno'
      }
    }

  }
}