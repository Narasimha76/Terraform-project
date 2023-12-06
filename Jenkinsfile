pipeline {
    agent any
    
    environment {
        AWS_ACCESS_KEY_ID     = credentials('AccesskeyID')
        AWS_SECRET_ACCESS_KEY = credentials('Secretaccesskey')
        AWS_REGION = "us-east-1"
    }

    stages {
        stage("Checkout from GIT") {
            steps {
                git branch: 'main', credentialsId: '04da37c2-3920-4970-bb93-3a7456f3551b', url: 'https://github.com/Madeep9347/Terraform-Infrastructure-Project.git'
            }
        }
        
        stage("Terraform Init") {
            steps {
                script {
                    //sh 'terraform init -input=false'
                    sh 'terraform init -reconfigure'


                }
            }
        }

        stage("Terraform Format") {
            steps {
                script {
                    sh 'terraform fmt'
                }
            }
        }

        stage("Terraform Validate") {
            steps {
                script {
                    sh 'terraform validate'
                }
            }
        }

        stage("Terraform Plan") {
            steps {
                script {
                    sh 'terraform plan'
                }
            }
        }

        stage("Terraform Apply") {
            steps {
                script {
                    sh 'terraform apply --auto-approve'
                    //sh 'terraform destroy --auto-approve'
                }
            }
        }
    }
}
