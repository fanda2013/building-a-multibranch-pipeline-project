pipeline {
  agent {
    docker {
      args '-p 3000:3000'
      image 'node'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }

    stage('test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }

    stage('123') {
      steps {
        sh './jenkins/scripts/deliver-for-development.sh'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }

  }
}