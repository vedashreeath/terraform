pipeline {
    agent any 
    environment{
    AWS_ACCESS_KEY_ID = credentials('AWS-creds')
    AWS_SECRET_ACCESS_KEY = credentials('AWS-creds')
    }
    stages {
        stage('Checkout the source code') {
            steps {
                git (
                    url: 'https://github.com/vedashreeath/terraform.git',
                    branch: 'master'
                )
            }
        }
        stage('Terraform run') {
            steps {
                script {
                    sh terraform init
                    sh terraform plan
                    sh terraform apply -auto-approve
                }
            }
        }
    }
}
