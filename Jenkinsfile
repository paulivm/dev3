pipeline {
    agent any
    options {
        skipDefaultCheckout(true)
    }
    stages {
        stage('clean workspace') {
            steps {
                cleanWs()
            }
        }
        stage('checkout') {
            steps {
                checkout scm
            }
        }

      stage('tfsec') {
            steps {
                script {               
                    bat 'docker --version'
                 }
                }
            }

       
        
    stage('Approval for Terraform') {
            steps {
                input(message: 'Approval required before Terraform', ok: 'Proceed', submitterParameter: 'APPROVER')
            }
        }

        stage('terraform') {
            steps {
                 bat 'C:\\terraform\\terraform.exe apply -auto-approve -no-color'
                }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
