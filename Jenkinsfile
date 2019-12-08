node{
  stage('SCM Checkout') {
    git 'https://github.com/monbostest/java-code1.git'
    }
  stage('compile code') {
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
   sh 'kubectl run myapp --image=nippy/myapp.$BUILD_NUMBER --restart=Never'
  }
  stage('Create Service to access '){
   sh 'kubectl expose pod myapp --port=8080 --type=LoadBalancer  --name=myapp'
  }
}
