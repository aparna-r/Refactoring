pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'building....'
      }
    }
    stage('sanity') {
      parallel {
        stage('pact tests') {
          steps {
            echo 'running pact tests...'
          }
        }
        stage('integration tests') {
          steps {
            echo 'running integration tests'
          }
        }
        stage('quality') {
          steps {
            echo 'running sonar qube scanning...'
          }
        }
        stage('security') {
          steps {
            echo 'run owasp scanning'
          }
        }
      }
    }
    stage('publish') {
      steps {
        echo 'publishing to artifactory...'
      }
    }
    stage('functional tests') {
      steps {
        echo 'running cucumber tests for UAT...'
      }
    }
    stage('release') {
      steps {
        echo 'release artifact and publish to artifactory...'
      }
    }
    stage('deploy') {
      steps {
        echo 'deploying to test...'
      }
    }
  }
}