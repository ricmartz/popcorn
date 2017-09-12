pipeline {
  agent any
  stages {
    stage('greeting') {
      steps {
        sh '''echo "hello world"
'''
      }
    }
    stage('build docker') {
      steps {
        sh '''docker build -t chyld/popcorn:$BUILD_NUMBER .
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