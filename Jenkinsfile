pipeline {
  agent any
  stages {
    stage('Build') {
      post {
        success {
          junit 'target/surefire-reports/**/*.xml'

        }

      }
      steps {
        sh 'mvn -Dmaven.test.failure.ignore=true install'
      }
    }
  }
  tools {
    maven 'maven-3.5.2'
    jdk 'jdk8'
  }
}