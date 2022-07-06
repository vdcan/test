pipeline {

  agent any
   
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/gaussic/SpringMVCDemo.git'
      }
    }
    stage('Maven Build') {
      steps {
        echo 'Building Maven...'
        bat 'mvn clean package'
      }
    }
    stage('Docker Build') {
      steps {
        echo 'Building Docker image...'
      }
    }
    stage('Docker Push') {
      steps {
        echo 'Pushing to Docker Registry...'
      }
    }
    
    stage('Kubernetes') {
      steps {
        echo 'Updating Kubernetes resources...'
      }
    }
  }
  environment {
    name01 = 'value01'
  }
}
