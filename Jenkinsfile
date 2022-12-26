pipeline{
    
    tools{
        maven 'mymaven'
    }
    
    agent any
    
    stages{
        
      stage('build the code'){
          steps{
              git 'https://github.com/Imran-shaik6/DevOpsCodeDemo.git'
              sh 'mvn package'
          }
      }
      
      stage('Deploy Code'){
          steps{
               git branch: 'main', url: 'https://github.com/Imran-shaik6/CICDdeploymentDemo.git'
              ansiblePlaybook credentialsId: 'ansiblehost', disableHostKeyChecking: true, installation: 'myansible', inventory: 'dev.inv', playbook: 'playbook1.yml'
          }
      }
    }
}
