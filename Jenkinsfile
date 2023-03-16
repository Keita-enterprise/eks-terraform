pipeline{
  agent any
  tools {
  terraform '/usr/location/bin'
}
  stages{
    
    stage('terraform init'){
      steps{
      sh 'terraform init'
      sh 'terraform plan'
      }
    }
  }
}
