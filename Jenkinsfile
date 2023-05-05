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
                    withCredentials([usernamePassword(credentialsId: 'ecbf154f-543d-4502-9cd1-f99e6fb83f66', passwordVariable: 'dockerhubpass', usernameVariable: 'dockerhubid ')]) {
                      sh 'docker login -u sachin887 -p ${dockerhubpass}'
                        sh 'docker build -t assignment/sachin1 .'
                    }
                   
                      sh "docker push assignment/sachin1:latest"
                }
            }
        }
  
         
    }
}
