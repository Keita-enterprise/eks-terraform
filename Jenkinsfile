pipeline{
  agent any
  environment{
AWS_ACCESS_KEY_ID = credentials('access_key')
  AWS_SECRET_ACCESS_KEY = credentials('scret_key')
  AWS_DEFAULT_REGION = "us-east-1"
  }
  stages{
    stage('Create an EKS Cluster'){
      steps{
        script{
          dir('Terraform-EKS-Cluster-with-Node-Group')
          sh 'terraform int'
          sh 'terraform apply -auto-approve'
        }
      }
    }
  }
  

}