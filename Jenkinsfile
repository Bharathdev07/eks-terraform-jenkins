pipeline {
    agent any
tools{
terraform 'terraform'
}
    stages {
        stage('Checkout') {
            steps {
                
                git branch: 'master', url: 'https://github.com/Bharathdev07/eks-terraform-jenkins.git'
            }
        }
        stage('Build') {
            steps {
                // Change directory to 'build'
                dir('eks') {
                    // Run a build command within the 'build' directory
                    sh 'terraform init'
                }
            }
        }
        stage('Test') {
            steps {
                // Change directory to 'test'
                dir('eks') {
                    // Run tests within the 'test' directory
                    sh 'terraform plan --var-file="dev.tfvars"'
                }
            }
        }
        stage('Deploy') {
            steps {
                // Change directory to 'deploy'
                dir('eks') {
                    // Deploy the application from the 'deploy' directory
                    sh 'terraform apply --auto-approve --var-file="dev.tfvars"'
                }
            }
        }
    }
}
