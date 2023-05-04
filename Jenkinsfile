pipeline {
    agent any

    environment {
        DOCKER_REGISTRY = "https://hub.docker.com/repository/docker/sachin887/assignment/general"
        DOCKER_USERNAME = credentials('sachin887')
        DOCKER_PASSWORD = credentials('Loveyoumom@07')
        IMAGE_NAME = "sachin1"
        IMAGE_TAG = "latest"
    }

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t $DOCKER_REGISTRY/$DOCKER_USERNAME/$IMAGE_NAME:$IMAGE_TAG .'
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD $DOCKER_REGISTRY"
                    sh "docker push $DOCKER_REGISTRY/$DOCKER_USERNAME/$IMAGE_NAME:$IMAGE_TAG"
                }
            }
        }
    }

    post {
        always {
            sh 'docker system prune -af'
        }
    }
}
