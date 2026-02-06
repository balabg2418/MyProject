def gv

pipeline {
    agent any
        parameters{
            string(name: 'Application', defaultValue: 'NA', description: 'Enter the name of the application to be deployed')
            choice(name: 'Version', choices: ['1.0', '2.0', '3.0'] , description: 'Select the version of the application to be deployed')
            booleanParam(name: 'Execute_TFapply' , defaultValue: true, description: 'Check this box to execute Terraform apply after the plan stage')
        }
    stages {
        stage("init") {
            steps {
                script{
                    gv = load "script.groovy"
                }
            }
        }
        stage("Checkout Code") {
            steps {
                // Checkout the Terraform code from the Git repository
                echo 'Checking out code from Git repository...'
            }
        }
        stage("Terraform Init") {
            steps {
                script {
                    gv.TFinit()
                }
            }
        }
        stage("Terraform Plan") {
            steps {
                script{
                    gv.TFplan()
                }
            }
        }
        stage("Terraform Apply") {
            when{
                expression {
                    return params.Execute_TFapply
                }
            }
            steps {
                echo 'Applying Terraform configuration...'
            }
        }
        stage("Job Status") {
            steps {
                echo 'Job completed successfully'
            }
        }
    }
}