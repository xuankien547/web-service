pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('xuankien547-dockerhub')
    }
   
    stages {
        
         stage('Build docker file') {
            steps {
              sh 'docker-compose build'                
                 
            }
        }
        
    
    stage('Login Dockerhub') {
      steps{
          sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKER_CREDENTIALS_USR --password-stdin'
        
      }
    }
    
    stage('Push Dockerhub') {
        steps {
            sh 'docker push xuankien547/jenkins-build-nginx:latest'
            sh 'docker push xuankien547/jenkins-build-php:latest'
        }
    }
    
   
    // Uploading Docker images into AWS ECR
    // stage('Pushing to ECR') {
    //  steps{  
    //      script {
    //             sh "docker tag ${IMAGE_REPO_NAME_NGINX}:${IMAGE_NGINX_TAG} ${REPOSITORY_NGINX_URI}:$IMAGE_NGINX_TAG"
    //             sh "docker push ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME_NGINX}:${IMAGE_NGINX_TAG}"
    //             sh "docker tag ${IMAGE_REPO_NAME_PHP}:${IMAGE_PHP_TAG} ${REPOSITORY_PHP_URI}:$IMAGE_PHP_TAG"
    //             sh "docker push ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME_PHP}:${IMAGE_PHP_TAG}"
    //      }
    //     }
    //   }
    }
}