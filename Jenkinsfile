node{
  stage('SCM Checkout') {
    git 'https://github.com/monbostest/java-code1.git'
    }
  stage('Package  code') {
    sh 'mvn package'
    }
  stage('docker buid'){
   sh 'docker build -t nippy/myapp.$BUILD_NUMBER .'
  }
  stage('push'){
   sh 'docker login -u nippy -p Redhat@123456'
   sh 'docker push nippy/myapp.$BUILD_NUMBER'
  }
  stage('Deploy an Application'){
   sh 'docker run -d -p 5601:8080  nippy/myapp.$BUILD_NUMBER'
  }
  }
