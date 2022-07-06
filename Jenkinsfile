pipeline {

  agent any
  tools {
      maven 'MAVEN_HOME' 
      jdk 'JAVA_HOME' 
  }
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/hijmenfokker/kubernetes-jenkins-ci-cd.git'
      }
    }
    stage('Maven Build') {
      steps {
        echo 'Building Maven...'
        sh 'mvn clean package'
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
    stage('SonarQube') {
      steps {
        echo 'Uploading to Sonar...'
        withCredentials(bindings: [string(credentialsId: 'sonar.login', variable: 'TOKEN')]) {
          sh """
                      mvn sonar:sonar -Dsonar.host.url=http://52.226.67.67 -Dsonar.login=$TOKEN
                    """
        }
        
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