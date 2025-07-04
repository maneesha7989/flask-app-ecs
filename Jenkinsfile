pipeline{
  agent any;
  stages{
    stage('git checkout code'){
      git url: "https://github.com/maneesha7989/flask-app-ecs.git", branch: "main"
    }
    stage('Build Image'){
      sh "docker build -t Flask-app:v1 ."
    }
    stage('Deploy'){
      sh "docker run -d --build Flask-app:v1"
    }
    stage('Push to Docker'){
      sh "docker push maneeshaagni/pandulurepo/Flash-app:v1"
    }
    stage('done'){
      echo "Pipeline Successfull !!"
    }
  }
}
