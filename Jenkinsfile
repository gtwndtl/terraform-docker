pipeline {
  agent any

  environment {
    TF_IN_AUTOMATION = "true"
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/gtwndtl/terraform-docker.git'
      }
    }

    stage('Terraform Init') {
      steps {
        dir('terraform') {  // เปลี่ยนไปยังโฟลเดอร์ terraform
          sh 'terraform init'
        }
      }
    }

    stage('Terraform Plan') {
      steps {
        dir('terraform') {  // เปลี่ยนไปยังโฟลเดอร์ terraform
          sh 'terraform plan'
        }
      }
    }

    stage('Terraform Apply') {
      steps {
        dir('terraform') {  // เปลี่ยนไปยังโฟลเดอร์ terraform
          sh 'terraform apply -auto-approve'
        }
      }
    }
  }

  post {
    always {
      echo 'Done!'
    }
  }
}
