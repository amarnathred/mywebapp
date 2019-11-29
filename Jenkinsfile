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

    stage('cde') {
      steps {
        sh 'scp /home/ubuntu/.jenkins/workspace/mywebapp_master/webapp/target/webapp.war ubuntu@172.31.29.5:/var/lib/tomcat8/webapps/test.war'
      }
    }

    stage('testing') {
      steps {
        git(url: 'https://github.com/selenium-saikrishna/FunctionalTesting.git', branch: 'master')
        sh 'java -jar /home/ubuntu/.jenkins/workspace/mywebapp_master/testing.jar'
      }
    }

    stage('delivery') {
      steps {
        sh 'scp /home/ubuntu/.jenkins/workspace/mywebapp_master/target/webapp.war ubuntu@172.31.21.193:/var/lib/tomcat8/webapps/proapp.war'
      }
    }

  }
}