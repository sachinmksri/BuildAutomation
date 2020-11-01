pipeline {
  agent any
  stages {
    stage('Development Build') {
      steps {
        echo 'Pull the code from the Git Repo'
        echo 'Create a Build Using Repo'
      }
    }

    stage('Smoke Tests') {
      steps {
        echo 'Run 2 Chrome Tests'
      }
    }

    stage('Deploy in QA') {
      steps {
        echo 'Stop the running server'
        echo 'Move the build to QA'
        echo 'Start the QA Server'
        echo 'Notify to QA by Email'
      }
    }

    stage('Integration Test') {
      parallel {
        stage('Integration Test') {
          steps {
            echo 'Sanity Tests (UI)'
          }
        }

        stage('API Test') {
          steps {
            echo 'Run REST Automation Tests'
          }
        }

        stage('Performance Testing') {
          steps {
            echo 'Run JMeter tests'
          }
        }

      }
    }

    stage('Certify') {
      when {
        branch 'master'
      }
      steps {
        echo 'QA Certified'
      }
    }

  }
}