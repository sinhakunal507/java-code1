node{
  stage('SCM Checkout') {
    git 'https://github.com/sinhakunal507/java-code1.git'
    }
  stage('Package  code') {
    sh 'mvn package'
    }
  stage('docker buid'){
   sh 'docker build -t sinhakunal507/drepo.$BUILD_NUMBER .'
  }
  stage('push'){
   sh 'docker login -u sinhakunal507 -p kunal21282'
   sh 'docker push sinhakunal507/drepo.$BUILD_NUMBER'
  }
  stage('Deploy an Application'){
   sh 'docker run -d -p 8080:8080  sinhakunal507/drepo.$BUILD_NUMBER'
  }
  }
