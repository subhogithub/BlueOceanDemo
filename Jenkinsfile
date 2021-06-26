pipeline {
  agent any
  stages {
    stage('CollectFromGit') {
      steps {
        git(url: 'https://github.com/subhogithub/simpleMavenJunit.git', branch: 'master', changelog: true, poll: true)
      }
    }

    stage('Compile') {
      steps {
        sh '''mvn clean
mvn compile'''
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }

    stage('Publish report') {
      steps {
        junit(testResults: '/target/surefire-reports/*.xml', allowEmptyResults: true)
      }
    }

  }
}