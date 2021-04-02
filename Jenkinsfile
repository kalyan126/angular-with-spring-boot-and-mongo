pipeline {
  agent any
  stages {
    stage('stage1') {
      parallel {
        stage('stage1') {
          steps {
            echo 'first step'
            git(url: 'https://github.com/kalyan126/angular-with-spring-boot-and-mongo.git', credentialsId: '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', branch: '*/master')
          }
        }

        stage('build') {
          steps {
            echo 'build- stage'
            sh '''mvn clean
mvn compile
mvn test
mvn package'''
          }
        }

        stage('artifacts') {
          steps {
            archiveArtifacts(artifacts: 'target/*.jar', caseSensitive: true)
            junit '/target/surefire-reports/*.xml'
          }
        }

      }
    }

  }
}