pipeline{
    
    agent any
    environment{
        PATH="/usr/share/maven/bin:$PATH"
    }
    stages{
        
        stage('Scm Checkout'){
            steps{
                
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'Github', url: 'https://github.com/sparsh27/new-maven.git']]])
            }
            
            }
        stage('Maven build') {
            
            steps{
                
                sh "mvn clean package"
            }
        } 
        stage('Maven Deploy'){
        
            steps{
                deploy adapters: [tomcat8(credentialsId: 'tomcatcred', path: '', url: 'http://localhost:5050')], contextPath: 'mywebapp', war: '**/*.war'
            
            }
        
        }
   
            
        }
    }
