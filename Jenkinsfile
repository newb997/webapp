pipeline {
  agent any

  triggers {
    pollSCM('* * * * *')
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', 
        url: 'https://github.com/newb997/webapp.git'
      }
    }
    stage('Build') {
      steps {
        sh '<MAVEN_BUILD_COMMAND>'
      }
    }
    stage('Test') {
      steps {
        sh '<MAVEN_TEST_COMMAND>'
      }
    }
    stage('Deploy') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'admin', url: 'http://192.168.56.102:8080/')], contextPath: null, war: 'path/to/war'
      }
    }
  }
}
