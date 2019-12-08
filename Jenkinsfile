node{
  stage('SCM Checkout') {
    git 'https://github.com/monbostest/java-code1.git'
    }
  stage('compile code') {
    sh 'mvn package'
    }
  stage('docker buid'){
   sh 'docker build -t nippy/myapp:3.0 .'
  }
  stage('push'){
   sh 'docker login -u nippy -p Redhat@123456'
   sh 'docker push nippy/myapp:2.0'
  }
  stage('Deploy an Application'){
   sh 'kubectl run myapp --image=nippy/myapp:3.0 --restart=Never'
  }
  stage('Create Service to access '){
   sh 'kubectl expose pod myapp --port=8080 --type=LoadBalancer  --name=myapp'
  }
}
