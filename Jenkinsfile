pipeline {
  agent any
  stages {
    stage('greeting') {
      steps {
        sh 'echo "hello world"'
      }
    }
    stage('build docker') {
      steps {
        sh '''docker build -t nzukoff/popcorn:$BUILD_NUMBER .


'''
      }
    }
    stage('docker push') {
      steps {
        sh '''docker login -u nzukoff -p
docker push nzukoff/popcorn:$BUILD_NUMBER'''
      }
    }
  }
}