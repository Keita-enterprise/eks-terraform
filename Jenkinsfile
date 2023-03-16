pipeline{
  agent any
  tools {
  terraform '/usr/location/bin'
}
  stages{
    stage('terraform init'){
      sh 'terraform init'
      sh 'terraform plan'
    }
  }
}
