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
        sh '''docker build -t ricmart/popcorn:$BUILD_NUMBER .
'''
      }
    }
    stage('testing') {
      steps {
        sh '''docker run ricmart/popcorn:$BUILD_NUMBER rails test
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
    stage('deply to k8s') {
      steps {
        sh '''envsubst < deployment.yaml | kubectl apply -f -
'''
      }
    }
  }
  environment {
    DOCKER_PASSWORD = credentials('DOCKER_PASSWORD')
  }
}