pipeline{
    
    tools{
        maven 'mymaven'
    }
    
    agent any
    
    stages{
        
        stage ('CloneRepo')
        {
            steps{
             echo 'This is stage 1'
              git 'https://github.com/Imran-shaik6/DevOpsCodeDemo.git'  
            }
        }
        
        stage ('Compile')
        {
            steps{
                
             sh  'mvn compile'
                
            }
        }
        stage ('CodeReview')
        {
            steps{
                
             sh  'mvn pmd:pmd'
                
            }
            post{
                success{
                    recordIssues(tools: [pmdParser(pattern: '**/pmd.xml')])
                }
            }
        }
        stage ('Test')
        {
            steps{
                
             sh  'mvn test'
                
            }
        post{
            success{
                junit 'target/surefire-reports/*.xml'
            }
        }
        }
        
        
      stage('build the code'){
          steps{
           
              sh 'mvn package'
          }
      }
      
      stage('Deploy Code'){
          steps{
               git branch: 'main', url: 'https://github.com/Imran-shaik6/CICDdeploymentDemo.git'
              ansiblePlaybook credentialsId: 'Ansiblehost', disableHostKeyChecking: true, installation: 'myansible', inventory: 'dev.inv', playbook: 'playbook1.yml'
          }
      }
    }
}
