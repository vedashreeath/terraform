pipeline {
    agent any 
    environment{
    AWS_ACCESS_KEY_ID = credentials('AWS-creds')
    AWS_SECRET_ACCESS_KEY = credentials('AWS-creds')
    DOCKERHUB_CREDENTIALS = credentials('Dockerhub-creds')
    }
    stages {
        stage('Checkout the source code') {
            steps {
                git (
                    url: 'https://github.com/vedashreeath/Devops-projects',
                    branch: 'master'
                )
            }
        }
        stage('build') {
            steps {
                dir('Project-1')
                sh 'docker build -t webimage'
                sh 'docker login -u ${DOCKERHUB_CREDENTIALS_USR} -p ${DOCKERHUB_CREDENTIALS_PSW}'
                sh 'docker push webimage'
            }
        }
            stage('Terraform run') {
            steps {
                script {
                    sh 'terraform init'
                    sh 'terraform plan'
                    sh 'terraform apply -auto-approve'
                }
            }
        }
    }
}
