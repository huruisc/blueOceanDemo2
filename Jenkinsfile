pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh '/home/maven/apache-maven-3.6.3/bin/mvn clean install'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            junit 'target/surefire-reports/TEST-*.xml'
          }
        }

        stage('dependency-check') {
          steps {
            dependencyCheck(additionalArguments: '--failOnCVSS 10 --format ALL', odcInstallation: 'dependency-check')
          }
        }

        stage('dependency-check-result') {
          steps {
            dependencyCheckPublisher(pattern: 'dependency-check-report.xml')
          }
        }

      }
    }

  }
}