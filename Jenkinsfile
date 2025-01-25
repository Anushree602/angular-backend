pipeline {
    agent any

    stages {
        stage('pull') {
            steps {
                git branch: 'dev', url: 'https://github.com/Anushree602/angular-backend.git'
            }
        }
             stage('build') {
            steps {
                sh 'mvn clean package' 
           }
        }
         stage('create docker file') {
            steps {
                sh '''
                docker build . -t anushree602/angular-backend:v1
                docker push anushree602/angular-backend:v1
                docker rmi anushree602/angular-backend:v1
                '''
           }
        }
              stage('deploy') {
            steps {
                sh 'kubectl apply -f ./yaml/' 
           }
        }
    }
}
