pipeline {
  agent any
  stages {
    stage('cd') {
      steps {
        git(url: 'https://github.com/amarnathred/maven.git', branch: 'master')
      }
    }

    stage('cb') {
      steps {
        sh 'mvn package'
      }
    }

  }
}