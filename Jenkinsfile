pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'compiling, unit tests, pmd, findbugs, checkstyle'
      }
    }
    stage('sanity') {
      parallel {
        stage('pact tests') {
          steps {
            echo 'running pact tests provided by tenants(quby)'
          }
        }
        stage('integration tests') {
          steps {
            echo 'running integration tests'
          }
        }
        stage('quality') {
          steps {
            echo 'running sonar qube scanning and check qaulity on sonarqube quality gate'
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
    stage('deploy') {
      steps {
        echo 'deploy to test/dev env...'
      }
    }
    stage('functional tests') {
      steps {
        echo 'running cucumber tests for UAT against dev/test env...'
      }
    }
    stage('release') {
      steps {
        echo 'release artifact and publish to artifactory...'
      }
    }
  }
}