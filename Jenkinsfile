pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''dotnet build eShopOnWeb-sln
'''
      }
    }

    stage('Test') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet test tests/UnitTests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test test/IntegrtionTests'
          }
        }

        stage('Functionnal') {
          steps {
            sh 'dotnet test tests/FunctionTests'
          }
        }

      }
    }

    stage('Deloyment ') {
      steps {
        sh 'dotnet publish eShopOnWeb-sln -o /var/aspnet'
      }
    }

  }
}