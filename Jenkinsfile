pipeline {
  agent any
  stages {
    stage('greetings') {
      steps {
        sh 'echo "Hello World"'
      }
    }
    stage('build docker') {
      steps {
        sh 'docker build -t popcorn:$BUILD_NUMBER .'
      }
    }
    stage('push docker') {
      steps {
        sh '''docker login - u ricmart -p ____
docker push ricmart/popcorn:$BUILD_NUMBER'''
      }
    }
  }
}