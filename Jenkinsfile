pipeline{
  agent any;
  stages{
    stage('git checkout code'){
      steps{
          git url: "https://github.com/maneesha7989/flask-app-ecs.git", branch: "main"
      }
    }
    stage('Build Image'){
       steps{
          sh "docker build -t flask-app:v1 ."
      }
    }
    stage('Deploy'){
      steps{
          sh "docker run -d -p 5000:5000 --name flask-app nginx:latest"
      }
    }
    stage('Push to Docker'){
      steps{
         withCredentials([usernamePassword(
           credentialsId: 'dockerhub-token', 
           passwordVariable: 'DOCKERHUB_CREDENTIALS_PSW', 
           usernameVariable: 'DOCKERHUB_CREDENTIALS_USR'
           
         )]){

        
         sh "docker login -u ${env.DOCKERHUB_CREDENTIALS_USR} -p ${env.DOCKERHUB_CREDENTIALS_PSW}"
         sh "docker image tag flask-app:v1 ${env.DOCKERHUB_CREDENTIALS_USR}/pandulurepo/one-tier-flask-app:v1"
         sh "docker push ${env.DOCKERHUB_CREDENTIALS_USR}/pandulurepo/one-tier-flask-app:v1"
         }
      }
    }
    stage('done'){
      steps{
          echo "Pipeline Successfull !!"
      }
    }
  }
}
