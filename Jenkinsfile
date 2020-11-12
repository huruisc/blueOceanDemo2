pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh '/home/maven/apache-maven-3.6.3/bin/mvn clean install'
      }
    }

    stage('test') {
      steps {
        junit 'target/surefire-reports/TEST-*.xml'
      }
    }

  }
}