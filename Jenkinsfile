pipeline {
  agent any
  stages {
    stage('helloworld') {
      agent any
      steps {
        sh 'echo "Hello World"'
        sh 'touch Dockerfile'
      }
    }

    stage('creating docker file ') {
      steps {
        sh '''echo "FROM centos:7" >Dockerfile
echo "RUN yum install httpd -y" >>Dockerfile

docker build -t pipelineimg .'''
      }
    }

    stage('Deployment') {
      steps {
        sh '''echo "Creating Container"

docker run -d -p 8000:80 --pipelineimg'''
      }
    }

  }
}