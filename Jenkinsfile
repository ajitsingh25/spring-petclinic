#!groovy

pipeline {
  agent none
  stages {
    stage('Checkout'){

          checkout scm
       }
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.5.0'
        }
      }
      steps {
        sh 'mvn clean install'
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
