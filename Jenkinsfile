pipeline {
  agent any
  stages {
    stage('greeting') {
      steps {
        sh '''echo "hello world"
'''
      }

stages {
    stage('testing') {
      steps {
        sh '''rails test
'''
      }      
      
    }
    stage('build docker') {
      steps {
        sh '''docker build -t ricmart/popcorn:$BUILD_NUMBER .
'''
      }
    }
    stage('docker push') {
      steps {
        sh '''docker login -u ricmart -p $DOCKER_PASSWORD
docker push ricmart/popcorn:$BUILD_NUMBER
'''
      }
    }
  }
  environment {
    DOCKER_PASSWORD = credentials('DOCKER_PASSWORD')
  }
}