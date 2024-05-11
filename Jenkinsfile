pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/imranshs08/eks-terraform-code.git'
            }
        }
        
        stage('TFLint') {
            steps {
                sh 'tflint'
            }
        }

        stage('TFSec') {
            steps {
                sh 'tfsec'
            }
        }

        stage('Deploy') {
            steps {
                // Initialize Terraform
                sh 'terraform init'

                // Format Terraform code
                sh 'terraform fmt -check=true -diff=true'

                // Plan Terraform changes
                sh 'terraform plan'

                // Apply Terraform changes
                sh 'terraform apply -auto-approve'
            }
        }
    }
}

