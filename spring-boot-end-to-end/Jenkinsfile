pipeline{
    agent any 
   tools {
  maven 'maven'
}
environment{
    nrepos="12bk/springboot-angular"
}
stages{
   stage('SourceCode'){
       steps{
           git 'https://github.com/I2BKeit/spring-boot-end-to-end.git'
       }
   } 
   stage('BuildArtifact'){
       steps{
            sh 'mvn package'
       }
      
   }
   stage('BuildImage'){
       steps{
           script{
               sh 'docker build -t $nrepos .'
             
           }
       }
   }
   stage("PushToDockerhub"){
       steps{
           withCredentials([string(credentialsId: 'dockerhub1', variable: 'password')]) {
    sh 'docker login -u 12bk -p ${password}'
    sh 'docker push ${nrepos}'
}
       }
   }
   stage("Deploy to kubernete"){
       steps{
           withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'kubeConfig', namespace: '', restrictKubeConfigAccess: false, serverUrl: '') {
    // some block
    sh 'kubectl apply -f eks-deploy-from-ecr.yaml'
}
           
       }
   }
  
}




}

