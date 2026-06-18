pipeline {
    agent any
     environment {
         AWS_REGION = 'us-east-1'
         ECR_REPO= '459364747993.dkr.ecr.us-east-1.amazonaws.com/devops-app-repo'
     }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }  

          stage ('Docker build'){
              steps {
                sh 'docker build -t spring-petclinic:latest .'
        }
    }
          stage('Docker push') {
            steps {
                 sh '''
                aws ecr get-login-password --region $AWS_REGION | \
                docker login --username AWS --password-stdin $ECR_REPO

                docker tag spring-petclinic:latest $ECR_REPO:latest

                docker push $ECR_REPO:latest
                '''
            }
          }
  }
}    
