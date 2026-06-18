pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }  

          stage ('Docker build'){
              steps {
                sh 'docker buils -t spring-petclinic:latest.'
        }
    }
  }
}    
