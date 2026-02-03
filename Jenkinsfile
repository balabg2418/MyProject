pipeline {
    agent any
    stages {
        stage("Checkout Code") {
            steps {
                // Checkout the Terraform code from the Git repository
                git branch: 'main', credentialsId: 'bg', url: 'https://github.com/balabg2418/MyProject.git'
            }
        }
        stage("Terraform Init") {
            steps {
                // Initialize Terraform to download providers and set up the backend
                sh 'terraform init'
            }
        }
        stage("Terraform Plan") {
            steps {
                // Generate and show an execution plan
                sh 'terraform plan'
            }
        }
        stage("Terraform Apply") {
            steps {
                // Apply the changes to create/update AWS infrastructure
                // --auto-approve flag is used for automation in CI/CD
                sh 'terraform apply'
            }
        }
        stage("Job Status") {
            steps {
                echo 'Job completed successfully'
            }
        }
    }
}
