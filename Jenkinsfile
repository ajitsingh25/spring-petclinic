#!groovy

pipeline {
  agent none
  stages {
    stage('Maven Install') {
      agent any
      steps {
        sh 'mvnw clean install'
      }
    }
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t ajitsingh25/spring-petclinic:latest .'
      }
    }
  }
}
