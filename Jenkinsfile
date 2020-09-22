pipeline{
    
    agent any
    environment{
        PATH="/usr/share/maven/bin:$PATH"
    }
    stages{
        
        stage('Scm Checkout'){
            steps{
                
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'Github', url: 'https://github.com/sparsh27/multi_branch.git']]])
            }
            
            }
        stage('Maven build') {
            
            steps{
                
                sh "mvn compile"
            }
        } 
        stage('Maven Test'){
        
            steps{
                sh "mvn test"
            }
        
        }
        
        stage('Maven package'){
            steps{
                 sh "mvn package"
            }
        }
       
   
            
        }
    }
