pipeline {
  environment {
          // Use AWS credentials saved in Jenkins as secret text
          AWS_ACCESS_KEY_ID     = credentials('AWS_ACCESS_KEY_ID')
          AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
      }

  agent any

  stages {
    stage('terraform init') {
      // Initialize Terraform to download required providers and modules
      steps {
            sh 'terraform init'
      }
    }
    stage('terraform action') {
      // Create or teardown AWS infrastructure
      steps {
            sh 'terraform ${action} -auto-approve'
      }
    }
  }
}