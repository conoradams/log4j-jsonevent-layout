pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh "mvn clean install deploy -DaltDeploymentRepository=nexus.belfast.snapshots::default::http://bfs-pdt-nexus-1.kana-test.com:8081/nexus/content/repositories/lagan-snapshots"
      }
	  post {
        success {
          junit 'target/surefire-reports/**/*.xml'

        }

      }
    }
  }
  tools {
    maven 'maven-3.5.2'
    jdk 'jdk8'
  }
  triggers {
    // every fifteen minutes (perhaps at :07, :22, :37, :52)
    pollSCM('H/15 * * * *')
  }

  options {
    buildDiscarder(logRotator(numToKeepStr:'3'))
    disableConcurrentBuilds()
  }
}