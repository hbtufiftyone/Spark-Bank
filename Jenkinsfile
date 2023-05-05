pipeline {
    agent any
    stages {
    stage('git clone') {
            steps {
              git branch: 'main', url: 'https://github.com/hbtufiftyone/Spark-Bank'
            }
    }
         stage(' push image to hub'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'dockerhub', variable: 'passwd')]) {
                      sh 'docker login -u sachin887 -p ${passwd}'
                        sh 'docker build -t assignment/sachin1 .'
                    }
                   
                      sh "docker push assignment/sachin1:latest"
                }
            }
        }
  
         
    }
}
