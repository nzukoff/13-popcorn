pipeline {
  agent any

  environment {
	DOCKER_PASSWORD = credentials('DOCKER_PASSWORD')
  }

  stages {
    stage('greeting') {
      steps {
        sh 'echo "hello world"'
      }
    }
    stage('testing') {
      steps {
        sh '''rails test'''
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
        sh '''docker login -u nzukoff -p $DOCKER_PASSWORD
docker push nzukoff/popcorn:$BUILD_NUMBER'''
      }
    }
  }
}
