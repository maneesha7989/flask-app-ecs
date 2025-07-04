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
          sh "docker run -d --build flask-app:v1"
      }
    }
    stage('Push to Docker'){
      steps{
         sh "docker push maneeshaagni/pandulurepo/flash-app:v1"
      }
    }
    stage('done'){
      steps{
          echo "Pipeline Successfull !!"
      }
    }
  }
}
