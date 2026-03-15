pipeline {
 agent any

 stages {

  stage('Clone Repo') {
   steps {
    git 'https://github.com/yourusername/devops-java-cicd-project.git'
   }
  }

  stage('Build Maven') {
   steps {
    sh 'mvn clean package'
   }
  }

  stage('SonarQube Analysis') {
   steps {
    sh 'mvn sonar:sonar'
   }
  }

  stage('Docker Build') {
   steps {
    sh 'docker build -t yourdockerhub/java-devops-app .'
   }
  }

  stage('Docker Push') {
   steps {
    sh 'docker push yourdockerhub/java-devops-app'
   }
  }

  stage('Deploy to Kubernetes') {
   steps {
    sh 'kubectl apply -f k8s/'
   }
  }

 }
}